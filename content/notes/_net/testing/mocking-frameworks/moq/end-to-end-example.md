---
title: end-to-end example
date: 2023-11-01T00:00:00-06:00
draft: false
weight: 4
---

# Abstract
> Credit: https://methodpoet.com/unit-testing-with-moq/

These notes provide an end-to-end example of unit testing a system with Moq.

# Assumptions
Assume this system under test:
```cs
public interface IBookService
{
    string GetISBNFor(string bookTitle);
    IEnumerable<string> GetBooksForCategory(string categoryId);
}
public interface IEmailSender
{
    public void SendEmail(string to, string subject, string body);
}
public class AccountService
{
    private IBookService _bookService;
    private IEmailSender _emailSender;
    public AccountService(IBookService bookService, IEmailSender emailSender)
    {
        _bookService = bookService;
        _emailSender = emailSender;
    }
    public IEnumerable<string> GetAllBooksForCategory(string categoryId)
    {
        var allBooks = _bookService.GetBooksForCategory(categoryId);
        return allBooks;
    }
    public string GetBookISBN(string categoryId, string searchTerm)
    {
        var allBooks = _bookService.GetBooksForCategory(categoryId);
        var foundBook = allBooks
                        .Where(x => x.ToUpper().Contains(searchTerm.ToUpper()))
                        .FirstOrDefault();
        if (foundBook == null)
        {
            return string.Empty;
        }
        return _bookService.GetISBNFor(foundBook);
    }
    public void SendEmail(string emailAddress, string bookTitle)
    {
        string subject = "Awesome Book";
        string body = $"Hi,\n\nThis book is awesome: {bookTitle}.\nCheck it out.";
        _emailSender.SendEmail(emailAddress, subject, body);
    }
}
```

# Testing GetAllBooksForCategory
```cs
[Fact]
public void GetAllBooksForCategory_returns_list_of_available_books()
{
    // ARRANGE
    var bookServiceMock = new Mock<IBookService>();
    bookServiceMock.Setup(x => x.GetBooksForCategory("UnitTesting"))
                   .Returns(new List<string>
                   {
                       "The Art of Unit Testing",
                       "Test-Driven Development",
                       "Working Effectively with Legacy Code"
                   });

    // We get an AccountService instance, but we pass the mocked BookService.
    // We pass null for the IEmailSender because the GetAllBooksForCategory method doesn't send an email:
    var accountService = new AccountService(bookServiceMock.Object, null);

    // ACT
    IEnumerable<string> result = accountService.GetAllBooksForCategory("UnitTesting");
    
    // ASSERT
    bookServiceMock.Verify(x => x.GetBooksForCategory("UnitTesting"));
    Assert.Equal(3, result.Count());
}
```

# Testing GetBookISBN
```cs
[Fact]
public void GetBookISBN_founds_the_correct_book_for_search_term()
{
    // ARRANGE
    var bookServiceMock = new Mock<IBookService>();

    bookServiceMock.Setup(x => x.GetISBNFor("The Art of Unit Testing"))
                   .Returns("0-9020-7656-6");

    var accountService = new AccountService(bookServiceMock.Object, null);

    // ACT
    string result = accountService.GetBookISBN("UnitTesting", "art");

    // ASSERT
    bookServiceMock.Verify(x => x.GetISBNFor("The Art of Unit Testing"));
    Assert.Equal("0-9020-7656-6", result);
}
```