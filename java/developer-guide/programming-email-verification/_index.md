---
title: Programming Email Verification
type: docs
weight: 125
url: /java/programming-email-verification/
---


## **Using EmailValidator**
[EmailValidator](https://reference.aspose.com/email/java/com.aspose.email/EmailValidator) provides full support for validating email addresses. With the help of the [EmailValidator](https://reference.aspose.com/email/java/com.aspose.email/EmailValidator) class, different types of validation can be performed, including email syntax checking, email domain checking and checking user accounts with mail servers. The [ValidationPolicy](https://reference.aspose.com/email/java/com.aspose.email/ValidationPolicy) enumeration is used to set the validation policy level:

- SyntaxOnly validates the email address syntax.
- SyntaxAndDomain validates the email address syntax, then validate the domain.
## **Basic Validation Functionality**
Use [EmailValidator](https://reference.aspose.com/email/java/com.aspose.email/EmailValidator) to verify the validity of email addresses.
### **Validating Emails**
Aspose.Email's validation functionality can be used to validate email addresses, domain names and mail servers. The following code snippet shows you how to use [EmailValidator](https://reference.aspose.com/email/java/com.aspose.email/EmailValidator) to validate an email address.


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