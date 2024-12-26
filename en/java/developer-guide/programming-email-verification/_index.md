---
title: Programming Email Verification
ArticleTitle: Programming Email Verification
type: docs
weight: 125
url: /java/programming-email-verification/
---


## **Using EmailValidator**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) provides full support for validating email addresses. With the help of the [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) class, different types of validation can be performed, including email syntax checking, email domain checking and checking user accounts with mail servers. The [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy) enumeration is used to set the validation policy level:

- SyntaxOnly validates the email address syntax.
- SyntaxAndDomain validates the email address syntax, then validate the domain.
## **Basic Validation Functionality**
Use [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) to verify the validity of email addresses.
### **Validating Emails**
Aspose.Email's validation functionality can be used to validate email addresses, domain names and mail servers. The following code snippet shows you how to use [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) to validate an email address.


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
## **Validate Email Messages**

This functionality allows users to validate message files, ensuring adherence to specified formats and structures. It supports validation for files/streams in the following formats:

- **MIME Formats:** eml, emlx, mht
- **MAPI Formats:** msg, oft

Aspose.Email provides the following tools to perform the task:

- [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) method - validate messages using this method, providing a file path or stream as input.
- [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) class - encapsulates the results of the message validation process. Provides insights into the success of the validation, format type, and any encountered errors.
- [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) Enum - Enumerates different types of validation errors.

The code sample below demonstrates how to use these tools for message validation:

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
