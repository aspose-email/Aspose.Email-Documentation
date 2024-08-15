---
title: "Программирование верификации электронной почты"
url: /ru/java/programming-email-verification/
weight: 125
type: docs
---


## **Использование валидатора электронной почты**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) обеспечивает полную поддержку проверки адресов электронной почты. С помощью [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) класс, можно выполнять различные типы проверки, включая проверку синтаксиса электронной почты, проверку домена электронной почты и проверку учетных записей пользователей на почтовых серверах. [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy) перечисление используется для установки уровня политики валидации:

- SyntaxOnly проверяет синтаксис адреса электронной почты.
- SyntaxAndDomain проверяет синтаксис адреса электронной почты, а затем проверяет домен.
## **Базовая функциональность валидации**
Use [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) для проверки достоверности адресов электронной почты.
### **Проверка электронных писем**
Функциональность проверки Aspose.Email может использоваться для проверки адресов электронной почты, доменных имен и почтовых серверов. В следующем фрагменте кода показано, как использовать [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) для подтверждения адреса электронной почты.


~~~Java
EmailValidator ev = new EmailValidator();
ValidationResult[] result = new ValidationResult[] { null };
ev.validate("user@domain.com", result);
if (result[0].getReturnCode() == ValidationResponseCode.ValidationSuccess)
{
    System.out.println("the email address is valid.");
}
else
{
    System.out.println("the mail address is invalid,for the " + result[0].getMessage());
}
~~~
## **Подтверждение сообщений электронной почты**

Эта функция позволяет пользователям проверять файлы сообщений, обеспечивая соответствие указанным форматам и структурам. Она поддерживает проверку файлов/потоков в следующих форматах:

- **Форматы MIME:** эмель, эмикс, миф
- **Форматы MAPI:** сообщение, часто

Aspose.Email предоставляет следующие инструменты для выполнения задачи:

- [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) метод - проверяйте сообщения с помощью этого метода, указывая путь к файлу или поток в качестве входных данных.
- [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) class — инкапсулирует результаты процесса проверки сообщений. Предоставляет информацию об успешности проверки, типе формата и любых обнаруженных ошибках.
- [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) Enum — перечисляет различные типы ошибок валидации.

В приведенном ниже примере кода показано, как использовать эти инструменты для проверки сообщений:

```java
MessageValidationResult result = MessageValidator.validate(fileName);

// Check if validation is successful
if (!result.isSuccess()) {
    System.out.println("Validation failed.");

    // Check the format type
    if (result.getFormatType() == FileFormatType.Mht) {
        System.out.println("Format type is Mht.");
    }

    // Check and display errors
    System.out.println("Number of errors: " + result.getErrors().size());

    for (MessageValidationError error : result.getErrors()) {
        System.out.println("Error Type: " + error.getErrorType());
        System.out.println("Description: " + error.getDescription());
    }
} else {
    System.out.println("Validation successful.");
}
```