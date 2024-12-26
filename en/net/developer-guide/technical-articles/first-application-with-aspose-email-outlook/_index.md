---
title: First Application with Aspose.Email.Outlook
ArticleTitle: First Application with Aspose.Email.Outlook
type: docs
weight: 280
url: /net/first-application-with-aspose-email-outlook/
---


This section demonstrates how to use [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). We create a small application that loads an outlook message file (TestMessage.msg) and displays the subject, from and to addresses, and body content on a Windows form. Follow these steps to create your first application using Aspose.Email.Outlook.

1. In Visual Studio, on the **File** menu, select **New**, then **Project**.
1. Choose to create either C# or VB.NET Windows application.
1. Import the Aspose.Email DLL in the application by right-clicking **Reference** in the Solution Explorer. This will be a Windows-based application which will only show the information contained in the message file.
1. Create an instance of the [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage) class by giving the path of the message file.
1. Use the public properties to display the subject, from, to and body on the Windows controls.

The implementation of above steps is demonstrated below in the following code snippet. Use the following code behind the **Load Msg File** button or in the forms OnLoad event.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}
