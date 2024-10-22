---
title: "Programación de Verificación de Correo Electrónico"
url: /es/net/programming-email-verification/
weight: 140
type: docs
---


## **Uso de Aspose.Email.Verifications**

Aspose.Email.Verifications proporciona soporte completo para validar direcciones de correo electrónico. Con la ayuda de la clase Aspose.Email.Verifications.EmailValidator, se pueden realizar diferentes tipos de validación, incluyendo verificación de la sintaxis del correo electrónico, verificación del dominio del correo electrónico y verificación de cuentas de usuario con servidores de correo. La enumeración ValidationPolicy se utiliza para establecer el nivel de política de validación:

- SyntaxOnly valida la sintaxis de la dirección de correo electrónico.
- SyntaxAndDomain valida la sintaxis de la dirección de correo electrónico y luego el dominio.
- MailServer valida la dirección intentando conectarse al servidor de correo.
  
## **Aplicación de Ejemplo**

Aspose.Email.Verifications es un componente poderoso y útil para verificar la validez de direcciones de correo electrónico, nombres de dominio de correo electrónico y mucho más. Este artículo muestra cómo crear una aplicación utilizando Aspose.Email.Verifications. La aplicación de demostración verifica la validez de una dirección de correo electrónico.

Para crear una aplicación que utilice Aspose.Email.Verifications para verificar direcciones de correo electrónico:

- Abre Visual Studio.
- En el menú **Archivo**, haz clic en **Nuevo** y luego en **Proyecto**. Para simplificar, este será un programa de consola. Elige un proyecto en C# o VB.NET según prefieras.

|**Creando un nuevo proyecto**|
| :- |
|![todo:image_alt_text](programming-email-verification_1.png)|

- Agrega una referencia a la aplicación de consola.

|**Agregando una referencia a Aspose.Email**|
| :- |
|![todo:image_alt_text](programming-email-verification_2.png)|

- Navega hasta Aspose.Email.dll en el directorio Bin bajo el directorio de instalación de Aspose.Email.

El siguiente fragmento de código te muestra cómo validar una dirección de correo electrónico. Cuando se ejecuta el código, un mensaje anuncia si la dirección de correo electrónico es válida o no.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-EmailValidations-EmailValidations.cs" >}}

- Compila y ejecuta.

|**Ejecutando la aplicación.**|| 
| :- | :- |
|![todo:image_alt_text](programming-email-verification_3.png)| |

## **Funcionalidad Básica de Validación**

Utiliza Aspose.Email.Verifications para verificar la validez de direcciones de correo electrónico. Para este propósito, Aspose.Email.Verifications tiene la clase EmailValidator.

### **Validando Correos Electrónicos**

La funcionalidad de validación de Aspose.Email se puede utilizar para validar direcciones de correo electrónico, nombres de dominio y servidores de correo. El siguiente fragmento de código te muestra cómo utilizar EmailValidator para validar una dirección de correo electrónico.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-ValidatingEmails-ValidatingEmails.cs" >}}

### **Validando Dominio**

Aspose.Email.Verifications puede verificar la validez de un nombre de dominio.

### **Validando Servidor de Correo**

Aspose.Email.Verifications puede verificar la validez de un servidor de correo.