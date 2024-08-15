---
title: "Programación y verificación de correo electrónico"
url: /es/net/programming-email-verification/
weight: 140
type: docs
---


## **Uso de Aspose.Email.Verifications**

Aspose.Email.Verifications proporciona soporte completo para la validación de direcciones de correo electrónico. Con la ayuda de la clase Aspose.Email.Verifications.EmailValidator, se pueden realizar diferentes tipos de validación, como la comprobación de la sintaxis del correo electrónico, la comprobación del dominio del correo electrónico y la comprobación de las cuentas de usuario en los servidores de correo. La enumeración ValidationPolicy se usa para establecer el nivel de la política de validación:

- SyntaxOnly valida la sintaxis de la dirección de correo electrónico.
- SyntaxAndDomain valida la sintaxis de la dirección de correo electrónico y, a continuación, el dominio.
- MailServer valida la dirección intentando conectarse al servidor de correo.
 
## **Ejemplo de aplicación**

Aspose.Email.Verifications es un componente potente y útil para comprobar la validez de las direcciones de correo electrónico, los nombres de dominio de correo electrónico y mucho más. En este artículo se muestra cómo crear una aplicación con Aspose.Email.Verifications. La aplicación de demostración comprueba la validez de una dirección de correo electrónico.

Para crear una aplicación que utilice Aspose.Email.Verifications para verificar las direcciones de correo electrónico:

- Abra Visual Studio.
- En el **File** menú, haga clic **New** y luego **Project**. Para simplificar, este será un programa de consola. Elija el proyecto C# o VB.NET como desee.

|**Crear un nuevo proyecto**|
|: - |
|![todo:image_alt_text](programming-email-verification_1.png)|

- Añada una referencia a la aplicación de consola.

|**Agregar una referencia a Aspose.Email**|
|: - |
|![todo:image_alt_text](programming-email-verification_2.png)|

- Busque Aspose.Email.dll en el directorio Bin del directorio de instalación de Aspose.Email.

El siguiente fragmento de código muestra cómo validar una dirección de correo electrónico. Cuando se ejecuta el código, aparece un mensaje que indica si la dirección de correo electrónico es válida o no.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-EmailValidations-EmailValidations.cs" >}}

- Construye y ejecuta.

|**Ejecución de la aplicación.**||
|: - |: - |
|![todo:image_alt_text](programming-email-verification_3.png)| |

## **Funcionalidad básica de validación**

Utilice Aspose.Email.Verifications para verificar la validez de las direcciones de correo electrónico. Para ello, Aspose.Email.Verifications tiene la clase EmailValidator.

### **Validación de correos electrónicos**

La funcionalidad de validación de Aspose.Email se puede utilizar para validar direcciones de correo electrónico, nombres de dominio y servidores de correo. El siguiente fragmento de código muestra cómo usar EmailValidator para validar una dirección de correo electrónico.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-ValidatingEmails-ValidatingEmails.cs" >}}

### **Validación del dominio**

Aspose.Email.Verifications puede verificar la validez de un nombre de dominio.

### **Validación del servidor de correo**

Aspose.Email.Verifications puede verificar la validez de un servidor de correo.
