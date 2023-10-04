---
title: unit testing controllers
date: 2023-10-04T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/testing?view=aspnetcore-7.0  

Unit testing controller logic involves testing a single action (not the dependencies of that action).  It does not test filters, routing, model binding, or model validation (these aspects are tested in *integration testing*).

The example in these notes uses a *mock object framework*.  A *mock object* is a fabricated object with predetermined property and method behaviors used for testing. [Moq](https://www.nuget.org/packages/Moq/) is an example of such a framework.
* See also: [JustMockLite](https://github.com/telerik/JustMockLite)
* See also: [MyTested.AspNetCore.Mvc](https://github.com/ivaylokenov/MyTested.AspNetCore.Mvc)

# Example
Consider this controller with an `Index` action method:
```cs
public class HomeController : Controller
{
    private readonly IBrainstormSessionRepository _sessionRepository;

    public HomeController(IBrainstormSessionRepository sessionRepository)
    {
        _sessionRepository = sessionRepository;
    }

    public async Task<IActionResult> Index()
    {
        var sessionList = await _sessionRepository.ListAsync();

        var model = sessionList.Select(session => new StormSessionViewModel()
        {
            Id = session.Id,
            DateCreated = session.DateCreated,
            Name = session.Name,
            IdeaCount = session.Ideas.Count
        });

        return View(model);
    }

    public class NewSessionModel
    {
        [Required]
        public string SessionName { get; set; }
    }

    [HttpPost]
    public async Task<IActionResult> Index(NewSessionModel model)
    {
        if (!ModelState.IsValid) 
            return BadRequest(ModelState);
        else
        {
            await _sessionRepository.AddAsync(new BrainstormSession()
            {
                DateCreated = DateTimeOffset.Now,
                Name = model.SessionName
            });
        }

        return RedirectToAction(actionName: nameof(Index));
    }
}
```

Create test sessions:
```cs
private List<BrainstormSession> GetTestSessions()
{
    var sessions = new List<BrainstormSession>();
    sessions.Add(new BrainstormSession()
    {
        DateCreated = new DateTime(2016, 7, 2),
        Id = 1,
        Name = "Test One"
    });
    sessions.Add(new BrainstormSession()
    {
        DateCreated = new DateTime(2016, 7, 1),
        Id = 2,
        Name = "Test Two"
    });
    return sessions;
}
```

The unit test for this action:
1. Confirms a `ViewResult` is returned
2. Confirms the `ViewDataDictionary.Model` is a `StormSessionViewModel`
3. Confirms there are two brainstorming sessions stored in `ViewDataDictionary.Model`
```cs {hl_lines=[13,14,15]}
[Fact]
public async Task Index_ReturnsAViewResult_WithAListOfBrainstormSessions()
{
    // Arrange
    var mockRepo = new Mock<IBrainstormSessionRepository>();
    mockRepo.Setup(repo => repo.ListAsync()).ReturnsAsync(GetTestSessions());
    var controller = new HomeController(mockRepo.Object);

    // Act
    var result = await controller.Index();

    // Assert
    var viewResult = Assert.IsType<ViewResult>(result); // #1
    var model = Assert.IsAssignableFrom<IEnumerable<StormSessionViewModel>>(viewResult.ViewData.Model); // #2
    Assert.Equal(2, model.Count()); // #3
}
```

The unit test for the HTTP POst Index method:
1. Confirms that when `ModelState.IsValid` is `false`, the action method returns an HTTP 400 `ViewResult`
2. Confirms that when `ModelState.IsValid` is `true`:
   1. The `Add` method on the repository is called
   2. A `RedirectToActionResult` is returned
```cs {hl_lines=[17,18,36-39]}
[Fact]
public async Task IndexPost_ReturnsBadRequestResult_WhenModelStateIsInvalid()
{
    // Arrange
    var mockRepo = new Mock<IBrainstormSessionRepository>();
    mockRepo.Setup(repo => repo.ListAsync())
            .ReturnsAsync(GetTestSessions());
    var controller = new HomeController(mockRepo.Object);
    // adds errors to test the invalid model state
    controller.ModelState.AddModelError("SessionName", "Required");
    var newSession = new HomeController.NewSessionModel();

    // Act
    var result = await controller.Index(newSession);

    // Assert
    var badRequestResult = Assert.IsType<BadRequestObjectResult>(result); // #1
    Assert.IsType<SerializableError>(badRequestResult.Value); // #1
}

[Fact]
public async Task IndexPost_ReturnsARedirectAndAddsSession_WhenModelStateIsValid()
{
    // Arrange
    var mockRepo = new Mock<IBrainstormSessionRepository>();
    mockRepo.Setup(repo => repo.AddAsync(It.IsAny<BrainstormSession>()))
            .Returns(Task.CompletedTask)
            .Verifiable();
    var controller = new HomeController(mockRepo.Object);
    var newSession = new HomeController.NewSessionModel() { SessionName = "Test Name" };

    // Act
    var result = await controller.Index(newSession);

    // Assert
    var redirectToActionResult = Assert.IsType<RedirectToActionResult>(result); // #2.2
    Assert.Null(redirectToActionResult.ControllerName); // #2.2
    Assert.Equal("Index", redirectToActionResult.ActionName); // #2.2
    mockRepo.Verify(); // Fails the test if the expected method wasn't called (#2.1)
}
```