---
title: "Protocolo de extensiones de correo de Internet multipropósito"
url: /es/java/multipurpose-internet-mail-extensions-protocol/
weight: 20
type: docs
---


{{% alert color="primary" %}}

Las extensiones multipropósito de correo de Internet (MIME) son un estándar de Internet que amplía el formato del correo electrónico para admitir:

- texto en conjuntos de caracteres distintos de US-ASCII;
- archivos adjuntos que no sean de texto;
- cuerpos de mensajes de varias partes; y
- información de encabezado en conjuntos de caracteres no ASCII.

SMTP solo admite caracteres ASCII de 7 bits, lo que significa que solo admite una pequeña cantidad de idiomas. Los idiomas basados en el alfabeto latino funcionan bien en SMTP; otros idiomas no se muestran correctamente cuando se entrega el correo electrónico. Sin embargo, MIME amplía la compatibilidad con caracteres ASCII de SMPT para que se puedan enviar y mostrar correos electrónicos que utilicen otros conjuntos de caracteres, imágenes y sonidos. En general, todos los clientes de correo electrónico y servidores SMTP asignan correctamente los mensajes en formato MIME.

{{% /alert %}}
## **Descripción de los encabezados MIME**
Los encabezados MIME contienen información sobre el protocolo.
### **MIME-Version**
Esto indica que el mensaje tiene formato MIME. Aparece como:

Versión MIME: 1.0
### **Content-Type**
Esto indica el tipo de contenido del mensaje, dado como un par de tipos y subtipos: text/plain, text/html, por ejemplo. El tipo de contenido multiparte puede contener texto, HTML, archivos adjuntos, imágenes, audio, vídeo, etc.

Tipo de contenido: multiparte
### **Content-Transfer-Encoding**
Indica si se utiliza un esquema de codificación de binario a texto encima de la codificación especificada por el tipo de contenido. Si lo ha hecho, indica cuál. Aquí podemos especificar el tipo de codificación binaria, de 7 bits y de 8 bits.
### **Encoded-Word**
Los encabezados de los mensajes SMTP normalmente utilizan caracteres ASCII. Los caracteres que no sean ASCII deben utilizar la sintaxis de palabras codificadas en MIME en lugar de una cadena literal. El formato es:

"=? *charset* ? *encoding* ? *texto codificado* ?=".
### **Multipart-Messages**
Un mensaje MIME de varias partes contiene un límite en el encabezado del tipo de contenido. Este límite, que no debe aparecer en ninguna de las partes, se coloca entre las partes y al principio y al final del cuerpo del mensaje, de la siguiente manera:

**Versión MIME: 1.0**

~~~Java

 Content-type: multipart/mixed; boundary="frontier"

This is a multi-part message in MIME format.

--frontier

Content-type: text/plain

This is the body of the message.

--frontier

Content-type: application/octet-stream

Content-transfer-encoding: base64

PGh0bWw+CiAgPGhlYWQ+CiAgPC9oZWFkPgogIDxib2R5PgogICAgPHA+VGhpcyBpcyB0aGUg

Ym9keSBvZiB0aGUgbWVzc2FnZS48L3A+CiAgPC9ib2R5Pgo8L2h0bWw+Cg==

--frontier--

~~~

Cada parte consta de su propio encabezado de contenido y un cuerpo.
### **Subtipos multiparte**
El estándar MIME define varios subtipos de mensajes multiparte. El subtipo se especifica en el encabezado «Tipo de contenido» del mensaje general.

La siguiente es una lista de los subtipos más utilizados.

- Mixto: Multipart/Mixed se usa para enviar archivos con diferentes encabezados «Content-Type» en línea. Si envías imágenes u otros archivos de fácil lectura, la mayoría de los clientes de correo los mostrarán en línea.
- Mensaje: una parte del mensaje contiene un mensaje de correo electrónico.
- Resumen: resumen es una forma sencilla de enviar varios mensajes de texto. El tipo de contenido predeterminado para cada parte es «message/rfc822\".
- Alternativa: el subtipo alternativo indica que cada parte es una versión «alternativa» del mismo contenido (o similar), cada una en un formato diferente indicado por su encabezado «Tipo de contenido».

La mayoría de las veces se usa multipart/alternative para el correo electrónico con dos partes, una de texto plano (text/plain) y una HTML (text/html). La parte de texto sin formato proporciona compatibilidad con versiones anteriores, mientras que la parte HTML permite el uso de formatos e hipervínculos. La mayoría de los clientes de correo electrónico ofrecen al usuario la opción de preferir el texto sin formato en lugar del HTML; este es un ejemplo de cómo los factores locales pueden afectar a la forma en que una aplicación elige qué parte del mensaje es la «mejor» para mostrar.

{{% alert color="primary" %}}

Para obtener más información, siga estos enlaces a los archivos de RFC.

- [RFC2045](https://www.rfc-archive.org/getrfc.php?rfc=2045#gsc.tab=0)
- [RFC131](https://www.rfc-archive.org/getrfc.php?rfc=131#gsc.tab=0)

{{% /alert %}}
