---
title: mailkit
date: 2022-01-21T14:22:06-0700
draft: false
---

# [MailKit](https://github.com/jstedfast/MailKit)
A cross-platform mail client library built on top of [MimeKit](https://www.mimekit.net/).

# Package
```powershell
dotnet add package mailkit
```

# Creating Messages
```cs

var message = new MimeMessage();
message.From.Add(new MailboxAddress("Joey", "joey@friends.com"));
message.To.Add(new MailboxAddress("Alice", "alice@wonderland.com"));
message.Subject = "How you doing?";

message.Body = new TextPart("plain") 
{
    Text = @"Hey Alice,

    What are you up to this weekend? Monica is throwing one of her parties on
    Saturday and I was hoping you could make it.
};
```

# Creating a text/html and text/plain Message
```cs
var attachment = CreateImageAttachment ();
var plain = CreateTextPlainPart ();
var html = CreateTextHtmlPart ();

// Note: it is important that the text/html part is added second, because it is the most expressive version and (probably) the most faithful to the sender's WYSIWYG editor.
var alternative = new MultipartAlternative ();
alternative.Add (plain);
alternative.Add (html);

// now create the multipart/mixed container to hold the multipart/alternative and the image attachment
var multipart = new Multipart ("mixed");
multipart.Add (alternative);
multipart.Add (attachment);

// now set the multipart/mixed as the message body
message.Body = multipart;
```

# Creating Attachments
```cs
// create an image attachment for the file located at path
var attachment = new MimePart("image", "gif") 
{
    Content = new MimeContent(File.OpenRead(path), ContentEncoding.Default),
    ContentDisposition = new ContentDisposition(ContentDisposition.Attachment),
    ContentTransferEncoding = ContentEncoding.Base64,
    FileName = Path.GetFileName(path)
};

// now create the multipart/mixed container to hold the message text and the image attachment
var multipart = new Multipart("mixed");
multipart.Add(body);
multipart.Add(attachment);

// now set the multipart/mixed as the message body
message.Body = multipart;
```

# `MailKit.Net.Smtp.SmtpClient`
```cs
public static void SendMessages (IList<MimeMessage> messages)
{
    using (var client = new SmtpClient()) 
    {
        client.Connect("smtp.gmail.com", 465, SecureSocketOptions.SslOnConnect);

        client.Authenticate("username", "password");

        foreach (var message in messages) 
            client.Send(message);

        client.Disconnect (true);
    }
}
```

`MailKit.Security.SecureSocketOptions`
| None                    | 0   | No SSL/TLS.                                                                                                          |
| ----------------------- | --- | -------------------------------------------------------------------------------------------------------------------- |
| `Auto`                  | 1   | Allow IMailService to decide which to use. If server does not support either, connection continues unencrypted.      |
| `SslOnConnect`          | 2   | Use SSL or TLS immediately.                                                                                          |
| `StartTls`              | 3   | Elevate to TLS immediately after reading greeting/capabilities of server. If server does not support STARTTLS, fail. |
| `StartTlsWhenAvailable` | 4   | Elevate to TLS immediately after reading greeting/capabilities of server, but only if server supports STARTTLS.      |
