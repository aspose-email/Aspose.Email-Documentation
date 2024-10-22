---
title: "Extracción de Contenidos de Mensajes de Correos Electrónicos"
url: /es/java/extraccion-de-contenidos-de-mensajes-de-correos-electronicos/
weight: 30
type: docs
---

## **Mostrando Información del Correo Electrónico en Pantalla**

El [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información del encabezado (discutida en [Extracción de Encabezados de Correo Electrónico](#extracting-email-headers)) puede ser extraída y manipulada de diferentes maneras. Este artículo explica cómo mostrar en pantalla la información del encabezado de correo electrónico seleccionada y el cuerpo del correo electrónico.

1. Crea una instancia de **MailMessage**.
2. Carga un mensaje de correo electrónico en la instancia de **MailMessage**.
3. Muestra el contenido del correo electrónico en la pantalla.

El código a continuación demuestra cómo cargar un mensaje de correo electrónico y mostrar su contenido - de, para, asunto y cuerpo del correo electrónico - en pantalla.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Obteniendo la Fecha y Hora del Mensaje**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) puede ser utilizada para recuperar la fecha del mensaje en UTC o en la zona horaria local. Esta información puede ser resumida de la siguiente manera:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - devuelve la fecha en UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - devuelve la fecha en la zona horaria local
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Devuelve **true**, si **MailMessage.getDate()** está en la zona horaria local

## **Extracción de Encabezados de Correo Electrónico**

El encabezado de correo electrónico representa un conjunto estándar de campos de encabezado definidos por Internet y RFC incluidos en los mensajes de correo electrónico de Internet. Un encabezado de correo electrónico puede ser especificado utilizando la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Los tipos de encabezados comunes están definidos en la clase [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/). Es una clase sellada que funciona como una enumeración normal.

Para extraer encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase **MailMessage**.
2. Carga un mensaje de correo electrónico en la instancia de la clase **MailMessage**.
3. Después de que un mensaje de correo electrónico ha sido cargado, obtendremos su contenido en bruto. La clase **MailMessage** contiene propiedades como De, Para, Cc, Asunto, etc. Estas propiedades pueden ser extraídas de los encabezados.
4. Muestra el contenido en bruto.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Obtener Valores de Encabezado Decodificados**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Obtener y Modificar el Encabezado de Disposición de Recurso Vinculado**

El recurso vinculado puede ser accedido y manipulado programáticamente en el objeto del mensaje de correo electrónico. El método [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) de la clase [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) obtiene el encabezado Content-Disposition. El siguiente ejemplo de código demuestra cómo acceder y modificar el nombre del archivo del recurso vinculado:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Obtener el cuerpo HTML como texto plano**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) proporciona la función de extraer el cuerpo HTML del mensaje como texto plano. La clase **MailMessage** proporciona un método [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-) que devuelve el cuerpo HTML en texto plano. El método **GetHtmlBodyText** acepta un parámetro booleano que indica si el cuerpo debe contener URLs o no. Pasar el parámetro como verdadero indica que el cuerpo HTML debe contener URLs.

El siguiente fragmento de código demuestra el uso del método **GetHtmlBodyText** para extraer el cuerpo HTML del correo electrónico como texto plano.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}