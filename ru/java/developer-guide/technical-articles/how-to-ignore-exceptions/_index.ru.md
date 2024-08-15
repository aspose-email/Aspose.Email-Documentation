---
title: "Как игнорировать исключения"
url: /ru/java/how-to-ignore-exceptions/
weight: 290
type: docs
---


## **Поддержка игнорирования исключений**
[ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) класс предоставляет возможность игнорировать исключения:

### **Примеры кода:**

Настройте обратный вызов для обработки исключений:
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

Или используйте **alternative**:
~~~java
//Ignore all exceptions
ExceptionManager.setIgnoreAll(true);
~~~

Кроме того, вы можете установить обратный вызов для игнорируемых **журнал исключений**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== EXCEPTION IGNORED === " + message);
    }
});
~~~

Пользователь будет уведомлен о том, что исключение может быть проигнорировано сообщением об ошибке. Например:
~~~
Exceptioin message:

AsposeArgumentException: properties should not be empty.
If you want to ignore an exception and want to proceed further then you can use:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
Invalid TNEF Attachment will be interpreted as regular attachment.
~~~
