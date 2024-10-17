---
title: "FAQs"
url: /es/net/faqs/
weight: 210
type: docs
---

**Pregunta**

¡Hola! para el siguiente código:

``` java

 Aspose.Email.Mime.ContentType ct = new Aspose.Email.Mime.ContentType();

ct.MediaType = "application/msword";

ct.CharSet = "ISO-2022-JP";

Attachment att = new Attachment("Test.doc", ct);

Console.WriteLine(att.ContentType.Name);

```

att.ContentType.Name devuelve el nombre del documento adjunto. ¿Es este un comportamiento esperado?

**Respuesta**: 
Sí, es un comportamiento esperado. Si ContentType.Name no se establece explícitamente, se tomará el valor del nombre del archivo como nombre.

**Pregunta:**

¿Por qué ExchangeWebServiceClient.FetchMessage convierte las imágenes incrustadas en adjuntos?

**Respuesta**: 
Microsoft Exchange Server tiene una funcionalidad como '[Conversión de Contenido](http://technet.microsoft.com/en-us/library/bb232174\(EXCHG.80\).aspx), que es el proceso de formatear correctamente un mensaje para cada destinatario. La decisión de realizar la conversión de contenido en un mensaje depende del destino y del formato del mensaje que se está procesando.

En otras palabras, para clientes desconocidos, el servidor puede realizar el formateo de mensajes de acuerdo con la configuración del servidor (para seleccionar el formato de mensaje más apropiado). Como entenderás, el formato más universal para cualquier cliente es 'text/plain' y estas configuraciones son configurables en el servidor.

Ten en cuenta: Outlook es un cliente de correo electrónico bien conocido para Microsoft Exchange Server (en caso de que MS Outlook tenga una versión más antigua que el servidor). Esto significa que el servidor Exchange pasa el formato del mensaje de acuerdo con las capacidades de Outlook. En nuestro caso, cuando ExchangeWebServiceClient intenta recuperar el mensaje, las capacidades de nuestros componentes son desconocidas para MS Exchange. El servidor pasa el mensaje a los componentes en el formato más simple (text/plain). En otras palabras, no hay partes html en la respuesta del servidor. En esta situación, las imágenes se incluyen en el mensaje como adjuntos.

Hay una manera de evitar el problema descrito. Si el mensaje en el servidor tiene Content-Type: multipart/alternative y una de sus partes es text/plain, en este caso, este mensaje se pasa al cliente tal cual. Las imágenes en este caso se muestran en el cuerpo del mensaje porque el mensaje también contiene una parte html. En el escenario actual, el mensaje se agrega a MS Exchange con ayuda de MS Outlook y, como resultado, el Content-Type del mensaje no es 'multipart/alternative'. Como resultado, tenemos un problema cuando intentamos recuperar el mensaje. Por ejemplo, aquí hay muestras de problemas similares: uno(<http://support.risualblogs.com/blog/2011/02/24/html-mails-sent-via-owa-and-outlook-2011-are-received-as-plain-text-mails-externally/>), dos(<http://forums.mozillazine.org/viewtopic.php?f=39&t=628678>), tres(<http://stackoverflow.com/questions/4681798/how-do-i-send-html-multipart-alternative-from-exchange-web-services-2010-sp1)Como> conclusión, la situación que se describe en el problema (imágenes incluidas en el mensaje como adjuntos) no es un error de los componentes de aspose. Esta es una característica específica del servidor Exchange.

**Pregunta:** 
¿Cómo puedo extraer datos del adjunto "oleData.mso" que obtengo como resultado de leer un MapiMessage que tiene un objeto OLE incrustado en él?

**Respuesta**: 
Los archivos como "oleData.mso" se refieren al formato de archivo Microsoft Compound Document (MCDF) y, desafortunadamente, el soporte para tales archivos está más allá de la ocupación de Aspose.Email. Sin embargo, hay ciertas bibliotecas .NET de código abierto, por ejemplo OpenMCDF, que se pueden utilizar para leer el contenido de tales archivos para guardarlo en disco.

**Pregunta:** 
¿Podemos escribir en el mismo archivo PST en hilos paralelos utilizando los mismos objetos?

**Respuesta:** 
No, la seguridad de los hilos no está garantizada en este caso. La escritura de mensajes debe hacerse en un solo hilo. Sin embargo, el producto debe funcionar correctamente con diferentes objetos de diferentes hilos.