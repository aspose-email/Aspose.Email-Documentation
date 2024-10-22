---
title: "Preguntas Frecuentes"
url: /es/java/faqs/
weight: 220
type: docs
---

**Pregunta**

¡Hola! para el siguiente código:

~~~Java

ContentType ct = new ContentType();

ct.setMediaType("application/msword");

ct.setCharSet("ISO-2022-JP");

Attachment att = new Attachment("Test.doc", ct);

System.out.println(att.getContentType().getName());

~~~

att.getContentType().getName() devuelve el nombre del documento adjunto. ¿Es este un comportamiento esperado?

**Respuesta**: 
Sí, es un comportamiento esperado. Si getContentType().getName() no se establece explícitamente, se tomará el valor del nombre del archivo como nombre.

**Pregunta:** 
¿Cómo extraigo datos del archivo adjunto "oleData.mso" que obtengo como resultado de leer un MapiMessage que tiene un objeto OLE incrustado en él?

**Respuesta**: 
Archivos como "oleData.mso" se refieren al formato de archivo Microsoft Compound Document (MCDF) y, desafortunadamente, el soporte para tales archivos está más allá de la ocupación de Aspose.Email. Sin embargo, hay ciertas bibliotecas de .NET de código abierto, por ejemplo OpenMCDF, que se pueden usar para leer el contenido de tales archivos para guardar en disco.

**Pregunta:** 
¿Podemos escribir en el mismo archivo PST en hilos paralelos utilizando los mismos objetos?

**Respuesta:** 
No, la seguridad en hilos no está garantizada en tal caso. La escritura de mensajes debe hacerse en un solo hilo. Sin embargo, el producto debe funcionar correctamente con diferentes objetos de diferentes hilos.