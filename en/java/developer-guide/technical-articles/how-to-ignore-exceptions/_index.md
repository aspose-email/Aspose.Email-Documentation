---
title: How to Ignore Exceptions
ArticleTitle: How to Ignore Exceptions
type: docs
weight: 290
url: /java/how-to-ignore-exceptions/
---


## **Ignore Exception Support**
[ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) class provide ignore exceptions ability:

### **Code examples:**

Set a callback to handle exceptions:
~~~java
ExceptionManager.setIgnoreExceptionsHandler(new IgnoreExceptionsCallback() {
    //exception path: {Module}\{Method}\{Action}\{GUID}
    //example: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598
    public boolean invoke(AsposeException ex, String path) {
        //Ignore all exceptions on MailMessage.Load
        return path.equals("MailMessage\\Load");
    }
});
~~~

Or use an **alternative**:
~~~java
//Ignore all exceptions
ExceptionManager.setIgnoreAll(true);
~~~

Also, you can set a callback for ignored **exceptions log**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== EXCEPTION IGNORED === " + message);
    }
});
~~~

The user will be notified, that the exception can be ignored by an error message. For example:
~~~
Exceptioin message:

AsposeArgumentException: properties should not be empty.
If you want to ignore an exception and want to proceed further then you can use:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
Invalid TNEF Attachment will be interpreted as regular attachment.
~~~
