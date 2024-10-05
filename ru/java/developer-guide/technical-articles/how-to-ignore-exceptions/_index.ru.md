---
title: "Как игнорировать исключения"
url: /ru/java/how-to-ignore-exceptions/
weight: 290
type: docs
---


## **Поддержка игнорирования исключений**
Класс [ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) предоставляет возможность игнорирования исключений:

### **Примеры кода:**

Установите обратный вызов для обработки исключений:
~~~java
ExceptionManager.setIgnoreExceptionsHandler(new IgnoreExceptionsCallback() {
    //путь исключения: {Module}\{Method}\{Action}\{GUID}
    //пример: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598
    public boolean invoke(AsposeException ex, String path) {
        //Игнорировать все исключения на MailMessage.Load
        return path.equals("MailMessage\\Load");
    }
});
~~~

Или используйте **альтернативу**:
~~~java
//Игнорировать все исключения
ExceptionManager.setIgnoreAll(true);
~~~

Также вы можете установить обратный вызов для игнорируемого **журнала исключений**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== ИСКЛЮЧЕНИЕ ИГНОРИРОВАНО === " + message);
    }
});
~~~

Пользователь будет уведомлён о том, что исключение может быть проигнорировано сообщением об ошибке. Например:
~~~
Сообщение об исключении:

AsposeArgumentException: свойства не должны быть пустыми.
Если вы хотите игнорировать исключение и хотите продолжить, то можете использовать:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
Неверное вложение TNEF будет интерпретировано как обычное вложение.
~~~