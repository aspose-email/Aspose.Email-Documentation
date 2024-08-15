---
title: "FAQs"
url: /es/java/faqs/
weight: 220
type: docs
---

**Question**

¡Hola! para el siguiente código:

~~~Java

ContentType ct = new ContentType();

ct.setMediaType("application/msword");

ct.setCharSet("ISO-2022-JP");

Attachment att = new Attachment("Test.doc", ct);

System.out.println(att.getContentType().getName());

~~~

att.getContentType () .getName () devuelve el nombre del documento adjunto. ¿Es este un comportamiento esperado?

**Answer**:
Sí, es un comportamiento esperado. Si getContentType () .getName () no se establece explícitamente, el valor del nombre del archivo se tomará como nombre.

**Question:**
¿Cómo extraigo los datos del archivo adjunto «OLEData.mso» que obtengo como resultado de leer un MAPIMessage que tiene un objeto OLE incrustado?

**Answer**:
Los archivos como «OLEData.mso» hacen referencia al formato de archivo de documentos compuestos (MCDF) de Microsoft y, lamentablemente, Aspose.Email no admite dichos archivos. Sin embargo, hay ciertas librerías.NET de código abierto, como OpenMCDF, que se pueden usar para leer el contenido de dichos archivos y guardarlos en un disco.

**Question:**
¿Podemos escribir en el mismo archivo PST en hilos paralelos usando los mismos objetos?

**Answer:**
No, la seguridad de la rosca no está garantizada en este caso. La escritura de los mensajes debe hacerse en un solo hilo. Sin embargo, el producto debe funcionar correctamente con diferentes objetos de diferentes hilos.
