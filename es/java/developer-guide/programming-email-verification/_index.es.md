---
title: "Programación de Verificación de Correo Electrónico"
url: /es/java/programming-email-verification/
weight: 125
type: docs
---


## **Uso de EmailValidator**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) proporciona soporte completo para validar direcciones de correo electrónico. Con la ayuda de la clase [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator), se pueden realizar diferentes tipos de validaciones, incluyendo la verificación de la sintaxis del correo electrónico, la verificación del dominio del correo electrónico y la verificación de cuentas de usuario con servidores de correo. La enumeración [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy) se utiliza para establecer el nivel de política de validación:

- SyntaxOnly valida la sintaxis de la dirección de correo electrónico.
- SyntaxAndDomain valida la sintaxis de la dirección de correo electrónico, y luego valida el dominio.
## **Funcionalidad Básica de Validación**
Utilice [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para verificar la validez de las direcciones de correo electrónico.
### **Validando Correos Electrónicos**
La funcionalidad de validación de Aspose.Email se puede utilizar para validar direcciones de correo electrónico, nombres de dominio y servidores de correo. El siguiente fragmento de código muestra cómo utilizar [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para validar una dirección de correo electrónico.


~~~Java
EmailValidator ev = new EmailValidator();
ValidationResult[] result = new ValidationResult[] { null };
ev.validate("user@domain.com", result);
if (result[0].getReturnCode() == ValidationResponseCode.ValidationSuccess)
{
    System.out.println("la dirección de correo electrónico es válida.");
}
else
{
    System.out.println("la dirección de correo es inválida, por: " + result[0].getMessage());
}
~~~
## **Validar Mensajes de Correo Electrónico**

Esta funcionalidad permite a los usuarios validar archivos de mensajes, asegurando la adherencia a formatos y estructuras especificados. Soporta validación para archivos/stream en los siguientes formatos:

- **Formatos MIME:** eml, emlx, mht
- **Formatos MAPI:** msg, oft

Aspose.Email proporciona las siguientes herramientas para llevar a cabo la tarea:

- Método [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) - valida mensajes utilizando este método, proporcionando una ruta de archivo o stream como entrada.
- Clase [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) - encapsula los resultados del proceso de validación de mensajes. Proporciona información sobre el éxito de la validación, tipo de formato y cualquier error encontrado.
- Enum [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) - Enumera diferentes tipos de errores de validación.

El siguiente ejemplo de código demuestra cómo usar estas herramientas para la validación de mensajes:

```java
MessageValidationResult result = MessageValidator.validate(fileName);

// Verificar si la validación fue exitosa
if (!result.isSuccess()) {
    System.out.println("La validación falló.");

    // Verificar el tipo de formato
    if (result.getFormatType() == FileFormatType.Mht) {
        System.out.println("El tipo de formato es Mht.");
    }

    // Verificar y mostrar errores
    System.out.println("Número de errores: " + result.getErrors().size());

    for (MessageValidationError error : result.getErrors()) {
        System.out.println("Tipo de Error: " + error.getErrorType());
        System.out.println("Descripción: " + error.getDescription());
    }
} else {
    System.out.println("Validación exitosa.");
}
```