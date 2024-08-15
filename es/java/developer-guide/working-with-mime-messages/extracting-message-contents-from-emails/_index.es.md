---
title: "Extraer el contenido de los mensajes de los correos electrónicos"
url: /es/java/extracting-message-contents-from-emails/
weight: 30
type: docs
---

## **Mostrar información de correo electrónico en la pantalla**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades de los mensajes de correo electrónico. La información del encabezado (que se explica en [Extracción de encabezados de correo electrónico](#extracting-email-headers)) pueden extraerse y manipularse de diferentes maneras. En este artículo se explica cómo mostrar la información del encabezado del correo electrónico seleccionado y el cuerpo del correo electrónico en la pantalla.

1. Crea una instancia del **MailMessage**.
2. Cargue un mensaje de correo electrónico en **MailMessage** instance.
3. Muestra el contenido del correo electrónico en la pantalla.

El código siguiente muestra cómo cargar un mensaje de correo electrónico y mostrar su contenido (origen, destino, asunto y cuerpo del correo electrónico) en la pantalla.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Obteniendo la fecha y hora del mensaje**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase se puede usar para recuperar la fecha del mensaje en UTC o en la zona horaria local. Esta información se puede resumir de la siguiente manera:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - devuelve la fecha en UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - devuelve la fecha en la zona horaria local
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Returns **true**, si **MailMessage.getDate()** está en la zona horaria local

## **Extracción de encabezados de correo electrónico**

El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y RFC que se incluye en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase. Los tipos de encabezados más comunes se definen en [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) clase. Es una clase sellada que funciona como una enumeración normal.

Para extraer los encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia del **MailMessage** class.
2. Cargue un mensaje de correo electrónico en la instancia de **MailMessage** class.
3. Una vez que se haya cargado un mensaje de correo electrónico, obtendremos su contenido sin procesar. El **MailMessage** la clase en sí contiene propiedades como From, To, Cc, Subject, etc. Estas propiedades se pueden extraer de los encabezados.
4. Muestra el contenido sin procesar.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Obtener valores de encabezado decodificados**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Obtenga y modifique el encabezado de disposición de recursos vinculados**

Se puede acceder al recurso vinculado y manipularlo mediante programación en el objeto de mensaje de correo electrónico. El [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) método del [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) la clase obtiene el encabezado Content-Disposition. El ejemplo de código siguiente muestra cómo acceder y modificar el nombre de archivo del recurso vinculado:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Obtener el cuerpo del HTML como texto sin formato**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase proporciona la función para extraer el cuerpo HTML del mensaje como texto sin formato. El **MailMessage** la clase proporciona una [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-) método que devuelve el cuerpo HTML en texto plano. El **GetHtmlBodyText** El método acepta un parámetro booleano que indica si el cuerpo debe contener URL o no. Si se pasa el parámetro como verdadero, se indica que el cuerpo del HTML debe contener direcciones URL.

El siguiente fragmento de código demuestra el uso de **GetHtmlBodyText** método para extraer el cuerpo HTML del correo electrónico como texto sin formato.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}
