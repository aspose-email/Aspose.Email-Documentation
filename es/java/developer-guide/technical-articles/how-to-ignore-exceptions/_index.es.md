---
title: "Cómo ignorar las excepciones"
url: /es/java/how-to-ignore-exceptions/
weight: 290
type: docs
---


## **Ignorar el soporte de excepciones**
[ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) la clase proporciona la capacidad de ignorar excepciones:

### **Ejemplos de código:**

Configure una devolución de llamada para gestionar las excepciones:
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

O usa un **alternative**:
~~~java
//Ignore all exceptions
ExceptionManager.setIgnoreAll(true);
~~~

Además, puede configurar una devolución de llamada para ignorados **registro de excepciones**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== EXCEPTION IGNORED === " + message);
    }
});
~~~

Se notificará al usuario que la excepción puede ignorarse mediante un mensaje de error. Por ejemplo:
~~~
Exceptioin message:

AsposeArgumentException: properties should not be empty.
If you want to ignore an exception and want to proceed further then you can use:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
Invalid TNEF Attachment will be interpreted as regular attachment.
~~~
