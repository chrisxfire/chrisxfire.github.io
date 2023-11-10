---
title: mocking httpclient
date: 2023-11-10T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Since `HttpClient` is not backed by an interface, the approach to get an `HttpClient` for testing is different:

1. Mock `HttpMessageHandler`:
    ```cs
    var handlerMock = new Mock<HttpMessageHandler>(MockBehavior.Strict);
    ```
2. Set up the mock:
    ```cs
    // Call Protected() since since HttpMessageHandler's constructor is protected:
    handlerMock.Protected()
            // Override HttpMessageHandler's protected internal abstract SendAsync method:
            .Setup<Task<HttpResponseMessage>>("SendAsync", ItExpr.IsAny<HttpRequestMessage>(), ItExpr.IsAny<CancellationToken>())
            .ReturnsAsync(new HttpResponseMessage()
            {
                StatusCode = HttpStatusCode.OK,
                Content = new StringContent(httpGetResponseStringContent)
            });
    ```
3. Pass the mocked `HttpMessageHandler` to the `HttpClient` constructor to get a test `HttpClient`:
    ```cs
    var httpClient = new HttpClient(handlerMock.Object);
    ```
4. Pass that `HttpClient` to the system under test that would normally receive an injected `HttpClient` instance:
    ```cs
    var sut = new SomeService(httpclient, ...);
    ```