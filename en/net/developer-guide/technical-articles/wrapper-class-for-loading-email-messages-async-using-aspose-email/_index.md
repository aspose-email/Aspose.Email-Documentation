---
title: Wrapper class for loading Email Messages Async using Aspose.Email
ArticleTitle: Wrapper class for loading Email Messages Async using Aspose.Email
type: docs
weight: 170
url: /net/wrapper-class-for-loading-email-messages-async-using-aspose-email/
---


## **Wrapper class for loading Email Messages**
There are a number of occurrences where it is desirable to have Time out functionality in order to abort an action that is taking unnecessary long time. This article provides a sample class to achieve the functionality of Time out functionality while loading EML/MSG files that could lead to very long delays or fail to load. Since Time out is not something directly related to disk or network read/write operation, it’s of little use to implement this feature within the API than have it implemented at the user end by writing a wrapper class around Aspose.

Canceling a long running thread can be achieved with the use of a wrapped delegate that passes out the thread, to be killed, in a local variable inside the method that initiated it. The long running thread is cancelled by aborting it and control is returned to the main application. The following code sample provides a sample wrapper class around the Aspose.Email library. The code follows sample usage of the wrapper class as well.
### **Programming Sample with .NET 3.5 and above**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage-WrapperMailMessage.cs" >}}
### **Programming Sample with .NET 2.0**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage_2_0-WrapperMailMessage.cs" >}}
### **Example Usage**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-UsingMailMessageWrapper-UsingMailMessageWrapper.cs" >}}
