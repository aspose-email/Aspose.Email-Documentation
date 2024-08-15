---
title: "FAQs"
url: /es/net/faqs/
weight: 210
type: docs
---

**Question**

¡Hola! para el siguiente código:

``` java

 Aspose.Email.Mime.ContentType ct = new Aspose.Email.Mime.ContentType();

ct.MediaType = "application/msword";

ct.CharSet = "ISO-2022-JP";

Attachment att = new Attachment("Test.doc", ct);

Console.WriteLine(att.ContentType.Name);

```

att.contentType.name devuelve el nombre del documento adjunto. ¿Es este un comportamiento esperado?

**Answer**:
Sí, es un comportamiento esperado. Si contentType.name no se establece explícitamente, el valor del nombre del archivo se tomará como nombre.

**Question:**

¿Por qué ExchangeWebServiceClient.fetchMessage convierte las imágenes incrustadas en archivos adjuntos?

**Answer**:
Microsoft Exchange Server tiene funciones como '[Conversión de contenido](http://technet.microsoft.com/en-us/library/bb232174\(EXCHG.80\).aspx), que es el proceso de formatear correctamente un mensaje para cada destinatario. La decisión de realizar la conversión del contenido de un mensaje depende del destino y del formato del mensaje que se esté procesando.

En otras palabras, para los clientes desconocidos, el servidor puede formatear los mensajes de acuerdo con la configuración del servidor (para seleccionar el formato de mensaje más apropiado). Como comprenderá, el formato más universal para cualquier cliente es «texto/simple» y estos ajustes se pueden configurar en el servidor.

Tenga en cuenta: Outlook es un conocido cliente de correo electrónico para Microsoft Exchange Server (en caso de que MS Outlook tenga una versión más antigua que el servidor). Esto significa que Exchange Server transfiere el formato del mensaje de acuerdo con las capacidades de Outlook. En nuestro caso, cuando ExchangeWebServiceClient intenta recuperar el mensaje, MS Exchange desconoce las capacidades de nuestros componentes. El servidor pasa el mensaje a los componentes en el formato más simple (text/plain). En otras palabras, no hay ninguna parte HTML en la respuesta del servidor. En esta situación, las imágenes se incluyen en los mensajes como archivos adjuntos.

Hay una forma de evitar el problema descrito. Si el mensaje del servidor tiene el tipo de contenido: multipart/alternativo y una de sus partes es texto/simple, en este caso este mensaje pasa al cliente tal como está. En este caso, las imágenes se muestran en el cuerpo del mensaje porque el mensaje también contiene una parte HTML. En el escenario actual, el mensaje se agrega a MS Exchange con la ayuda de MS Outlook y, por lo tanto, el tipo de contenido del mensaje no es «multiparte/alternativo». Como resultado, tenemos un problema cuando intentamos recuperar el mensaje. Por ejemplo, aquí hay ejemplos de problemas similares: one (<http://support.risualblogs.com/blog/2011/02/24/html-mails-sent-via-owa-and-outlook-2011-are-received-as-plain-text-mails-externally/>), dos (<http://forums.mozillazine.org/viewtopic.php?f=39&t=628678>), tres (<http://stackoverflow.com/questions/4681798/how-do-i-send-html-multipart-alternative-from-exchange-web-services-2010-sp1)As> En conclusión, la situación que se describe en el número (imágenes incluidas en el mensaje como archivos adjuntos) no es un error de aspose components. Esta es una característica específica del servidor Exchange.

**Question:**
¿Cómo extraigo los datos del archivo adjunto «OLEData.mso» que obtengo como resultado de leer un MAPIMessage que tiene un objeto OLE incrustado?

**Answer**:
Los archivos como «OLEData.mso» hacen referencia al formato de archivo de documentos compuestos (MCDF) de Microsoft y, lamentablemente, Aspose.Email no admite dichos archivos. Sin embargo, hay ciertas librerías.NET de código abierto, como OpenMCDF, que se pueden usar para leer el contenido de dichos archivos y guardarlos en un disco.

**Question:**
¿Podemos escribir en el mismo archivo PST en hilos paralelos usando los mismos objetos?

**Answer:**
No, la seguridad de la rosca no está garantizada en este caso. La escritura de los mensajes debe hacerse en un solo hilo. Sin embargo, el producto debe funcionar correctamente con diferentes objetos de diferentes hilos.
