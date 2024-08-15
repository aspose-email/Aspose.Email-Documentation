---
title: "Programación y verificación de correo electrónico"
url: /es/java/programming-email-verification/
weight: 125
type: docs
---


## **Uso de EmailValidator**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) proporciona soporte completo para la validación de direcciones de correo electrónico. Con la ayuda del [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) clase, se pueden realizar diferentes tipos de validación, incluida la comprobación de la sintaxis del correo electrónico, la comprobación del dominio del correo electrónico y la comprobación de las cuentas de usuario con los servidores de correo. El [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy) la enumeración se usa para establecer el nivel de la política de validación:

- SyntaxOnly valida la sintaxis de la dirección de correo electrónico.
- SyntaxAndDomain valida la sintaxis de la dirección de correo electrónico y, a continuación, valida el dominio.
## **Funcionalidad básica de validación**
Use [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para verificar la validez de las direcciones de correo electrónico.
### **Validación de correos electrónicos**
La funcionalidad de validación de Aspose.Email se puede utilizar para validar direcciones de correo electrónico, nombres de dominio y servidores de correo. El siguiente fragmento de código muestra cómo usar [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para validar una dirección de correo electrónico.


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
## **Validar mensajes de correo electrónico**

Esta funcionalidad permite a los usuarios validar los archivos de mensajes, garantizando el cumplimiento de los formatos y estructuras especificados. Admite la validación de archivos o transmisiones en los siguientes formatos:

- **Formatos MIME:** eml, emlx, mth
- **Formatos MAPI:** mensaje, a menudo

Aspose.Email proporciona las siguientes herramientas para realizar la tarea:

- [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) método: valida los mensajes con este método, proporcionando una ruta de archivo o una secuencia como entrada.
- [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) class: encapsula los resultados del proceso de validación de mensajes. Proporciona información sobre el éxito de la validación, el tipo de formato y cualquier error encontrado.
- [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) Enum: enumera los diferentes tipos de errores de validación.

El ejemplo de código que aparece a continuación muestra cómo usar estas herramientas para la validación de mensajes:

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