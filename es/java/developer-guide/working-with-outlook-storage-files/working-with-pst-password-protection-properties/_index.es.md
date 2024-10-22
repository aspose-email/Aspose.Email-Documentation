---
title: "Trabajando con las propiedades de protección de contraseña de PST"
url: /es/java/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

{{% alert color="primary" %}} 

Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección con contraseña en un archivo PST. Este artículo muestra cómo verificar un PST en busca de una contraseña y también cómo comprobar si la contraseña aplicada es correcta.

{{% /alert %}} 

## **Verificar la protección con contraseña**

El valor de [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) de la clase [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) se utiliza para comprobar si un archivo está protegido con contraseña.

El hash CRC-32 de la cadena de la contraseña se almacena en la propiedad PidTagPstPassword (tag = 0x67ff0003) en [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). Si esta propiedad existe y no es cero, entonces el PST está protegido por contraseña.

El siguiente fragmento de código muestra cómo comprobar si un archivo PST está protegido por contraseña y si la cadena dada es una contraseña válida para ese PST.

El fragmento de código a continuación muestra dos funciones, la primera comprueba si el PST está protegido por contraseña, y la segunda muestra cómo verificar si una contraseña proporcionada es correcta o no.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Eliminar/Restablecer la propiedad PR_PST_PASSWORD**

La eliminación de la propiedad [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) no se puede lograr como se eliminan otras propiedades de un almacén de mensajes. En su lugar, necesitamos establecer su valor en cero (0) para que se elimine. La propiedad "Store" de la clase PST permite el acceso a las propiedades del almacén de PST en lugar de las MessageStoreProperties de PST en este caso.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Establecer/Cambiar la contraseña de PST**

El siguiente fragmento de código muestra cómo establecer una contraseña en archivos PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Verificación de contraseña para archivos PST protegidos por contraseña**

Aspose.Email permite a los desarrolladores comprobar si el archivo PST está protegido por contraseña y verificar si la contraseña dada es correcta o no. Para esto, la API proporciona la propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) y el método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-). La propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) devuelve **true** si el archivo PST está protegido por contraseña y **false** si no lo está. El método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) toma la cadena de la contraseña como parámetro y devuelve **true** si la contraseña es correcta y false si es incorrecta.

El siguiente fragmento de código demuestra el uso de la propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) y el método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-).

### **Código de ejemplo**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Salida de consola**

El almacenamiento está protegido por contraseña - Verdadero
La contraseña es válida - Verdadero