---
title: "Программирование проверки электронной почты"
url: /ru/java/programming-email-verification/
weight: 125
type: docs
---


## **Использование EmailValidator**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) предоставляет полную поддержку проверки адресов электронной почты. С помощью класса [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) можно выполнять различные виды проверки, включая проверку синтаксиса электронной почты, проверку домена электронной почты и проверку учетных записей пользователей с почтовыми серверами. Для установки уровня политики проверки используется перечисление [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy):

- SyntaxOnly проверяет только синтаксис адреса электронной почты.
- SyntaxAndDomain проверяет синтаксис адреса электронной почты, затем проверяет домен.
## **Основная функциональность проверки**
Используйте [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) для проверки действительности адресов электронной почты.
### **Проверка электронной почты**
Функциональность проверки в Aspose.Email может быть использована для проверки адресов электронной почты, доменных имен и почтовых серверов. Следующий фрагмент кода показывает, как использовать [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) для проверки адреса электронной почты.


~~~Java
EmailValidator ev = new EmailValidator();
ValidationResult[] result = new ValidationResult[] { null };
ev.validate("user@domain.com", result);
if (result[0].getReturnCode() == ValidationResponseCode.ValidationSuccess)
{
    System.out.println("адрес электронной почты действителен.");
}
else
{
    System.out.println("адрес электронной почты недействителен, " + result[0].getMessage());
}
~~~
## **Проверка электронных сообщений**

Эта функциональность позволяет пользователям проверять файлы сообщений, обеспечивая соблюдение заданных форматов и структур. Она поддерживает проверку для файлов/потоков в следующих форматах:

- **Форматы MIME:** eml, emlx, mht
- **Форматы MAPI:** msg, oft

Aspose.Email предоставляет следующие инструменты для выполнения данной задачи:

- Метод [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) - проверяйте сообщения с помощью этого метода, предоставляя путь к файлу или поток в качестве ввода.
- Класс [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) - инкапсулирует результаты процесса проверки сообщения. Предоставляет информацию о успешности проверки, типе формата и любых обнаруженных ошибках.
- Перечисление [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) - перечисляет различные типы ошибок проверки.

Ниже приведен пример кода, демонстрирующий, как использовать эти инструменты для проверки сообщений:

```java
MessageValidationResult result = MessageValidator.validate(fileName);

// Проверка успешности валидации
if (!result.isSuccess()) {
    System.out.println("Проверка не прошла.");

    // Проверка типа формата
    if (result.getFormatType() == FileFormatType.Mht) {
        System.out.println("Тип формата Mht.");
    }

    // Проверка и вывод ошибок
    System.out.println("Количество ошибок: " + result.getErrors().size());

    for (MessageValidationError error : result.getErrors()) {
        System.out.println("Тип ошибки: " + error.getErrorType());
        System.out.println("Описание: " + error.getDescription());
    }
} else {
    System.out.println("Проверка успешна.");
}
```