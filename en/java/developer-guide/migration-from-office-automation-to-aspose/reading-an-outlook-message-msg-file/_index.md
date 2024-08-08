---
title: Reading an Outlook Message (MSG) file
type: docs
weight: 10
url: /java/reading-an-outlook-message-msg-file/
---


{{% alert color="primary" %}} 

Our migration tips show how Aspose products can be used to improve your applications and free you from dependency on traditional automation.

This migration tip shows how to read a Microsoft Outlook message file and display its contents on the screen using both [Microsoft Office Automation](#office-automation) and [Aspose.Email](#asposeemail-for-java) code. The sample code below only shows the contents on the console to give you an idea of how it works. Use the code snippets in your own Windows, web or other application.

{{% /alert %}} 
## **Office Automation**
To use Office Automation objects for Microsoft Outlook, you need to add references to Microsoft Office and Microsoft Office Interop for Outlook libraries to your project.
### **Programming Samples**
**C#**

~~~cs

// Add the namespaces

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Create a new Application Class

Application app = new Application();

// Create a MailItem object

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Access different fields of the message

System.Console.WriteLine(string.Format("Subject:{0}", item.Subject));

System.Console.WriteLine(string.Format("Sender Email Address:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("SenderName:{0}", item.SenderName));

System.Console.WriteLine(string.Format("TO:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Html Body:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Text Body:{0}", item.Body));


~~~
## **Aspose.Email for Java**
The following code snippet does the same thing as [the code above](/#office-automation) using Aspose.Email for Java.

To access the [Aspose.Email Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) objects, you need to add a reference to Aspose.Email to your project.
### **Programming Samples**

~~~java

// Create a new object of type MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Access the fields of the message
System.out.println("Subject: " + msg.getSubject());
System.out.println("Sender Email Address: " + msg.getSenderEmailAddress());
System.out.println("SenderName:{0}" + msg.getSenderName());
System.out.println("TO:{0}" + msg.getDisplayTo());
System.out.println("CC:{0}" + msg.getDisplayCc());
System.out.println("BCC:{0}" + msg.getDisplayBcc());
System.out.println("Html Body:{0}" + msg.getBodyHtml());
System.out.println("Text Body:{0}" + msg.getBody());
System.out.println("Rtf Body:{0}" + msg.getBodyRtf());


~~~
