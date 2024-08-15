---
title: "Trabajando con las propiedades de protección con contraseña de PST"
url: /es/java/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

{{% alert color="primary" %}}

Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección con contraseña en un archivo PST. Este artículo muestra cómo comprobar la contraseña de un PST y también cómo comprobar si la contraseña que se le ha aplicado es correcta.

{{% /alert %}}

## **Compruebe la protección con contraseña**

The [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) valor del [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) La clase se usa para comprobar si un archivo está protegido con contraseña.

El hash CRC-32 de la cadena de contraseña se almacena en la propiedad pidTagPstPassword (tag = 0x67ff0003) del [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). Si esta propiedad existe y no es cero, el PST está protegido con contraseña.

El siguiente fragmento de código muestra cómo comprobar si un archivo PST está protegido con contraseña y si la cadena indicada es una contraseña válida para ese PST.

El siguiente fragmento de código muestra dos funciones: la primera comprueba si el PST está protegido con contraseña y la segunda muestra cómo comprobar si la contraseña proporcionada es correcta o no.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Eliminar o restablecer la propiedad PR_PST_PASSWORD**

Eliminación del [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) no se puede obtener la propiedad porque se eliminan otras propiedades de un almacén de mensajes. En su lugar, necesitamos establecer su valor en cero (0) para eliminarla. La propiedad «Store» de la clase PST permite el acceso a las propiedades de la tienda de PST en lugar de a MessageStoreProperties de PST en este caso.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Establecer/cambiar la contraseña de PST**

El siguiente fragmento de código muestra cómo establecer una contraseña en los archivos PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Verificación de contraseña para archivos PST protegidos con contraseña**

Aspose.Email permite a los desarrolladores comprobar si el archivo PST está protegido con contraseña y comprobar si la contraseña dada es correcta o no. Para ello, la API proporciona [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) propiedad y [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) método. El [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) devoluciones de propiedades **true** si el archivo PST está protegido con contraseña y **false** si no lo es. El [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) método que toma la contraseña de cadena como parámetro y devuelve **true** si la contraseña es correcta y falsa, es incorrecta.

El siguiente fragmento de código demuestra el uso de [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) propiedad y [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) method.

### **Código de muestra**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Salida de consola**

El almacenamiento está protegido con contraseña: verdadero
La contraseña es válida: verdadera
