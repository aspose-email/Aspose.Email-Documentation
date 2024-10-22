---
title: "Protocolo de Extensiones de Correo de Internet Multicuerpo"
url: /es/java/protocolo-de-extensiones-de-correo-de-internet-multicuerpo/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Las Extensiones de Correo de Internet Multicuerpo (MIME) son un estándar de Internet que extiende el formato de correo electrónico para admitir:

- texto en conjuntos de caracteres distintos a US-ASCII;
- archivos adjuntos no textuales;
- cuerpos de mensajes multipartes; y
- información de encabezado en conjuntos de caracteres no ASCII.

SMTP solo admite caracteres ASCII de 7 bits, lo que significa que solo admite un número reducido de idiomas. Los idiomas basados en el alfabeto latino funcionan bien en SMTP; otros idiomas no se muestran correctamente cuando se entrega el correo electrónico. Sin embargo, MIME amplía el soporte de caracteres ASCII de SMTP para que se puedan enviar y mostrar correos electrónicos utilizando otros conjuntos de caracteres, imágenes y sonidos. Generalmente, todos los clientes de correo electrónico y servidores SMTP mapean correctamente los mensajes en formato MIME. 

{{% /alert %}} 
## **Comprendiendo los Encabezados MIME**
Los encabezados MIME contienen información sobre el protocolo.
### **MIME-Version**
Esto indica que el mensaje está en formato MIME. Aparece como:

MIME-Version: 1.0
### **Content-Type**
Esto indica el tipo de contenido del mensaje, dado como un par de tipo y subtipo: text/plain, text/html, por ejemplo. El tipo de contenido multipart puede contener texto, HTML, archivos adjuntos, imágenes, audio, video, etc. 

Content-Type: multipart
### **Content-Transfer-Encoding**
Indica si se utiliza un esquema de codificación de texto a binario por encima de la codificación especificada por el tipo de contenido. Si lo tiene, indica cuál. Aquí podemos especificar tipos de codificación de 7 bits, 8 bits y binaria. 
### **Encoded-Word**
Los encabezados de mensajes SMTP normalmente utilizan caracteres ASCII. Los caracteres no ASCII deben utilizar la sintaxis de palabra codificada MIME en lugar de una cadena literal. El formato es: 

"=? *charset* ? *encoding* ? *texto codificado* ?=". 
### **Multipart-Messages**
Un mensaje multipart MIME contiene un límite en el encabezado del tipo de contenido. Este límite, que no debe aparecer en ninguna de las partes, se coloca entre las partes, y al principio y al final del cuerpo del mensaje, como sigue:

**MIME-version: 1.0**

~~~Java

 Content-type: multipart/mixed; boundary="frontier"

Este es un mensaje multipart en formato MIME.

--frontier

Content-type: text/plain

Este es el cuerpo del mensaje.

--frontier

Content-type: application/octet-stream

Content-transfer-encoding: base64

PGh0bWw+CiAgPGhlYWQ+CiAgPC9oZWFkPgogIDxib2R5PgogICAgPHA+VGhpcyBpcyB0aGUg

Ym9keSBvZiB0aGUgbWVzc2FnZS48L3A+CiAgPC9ib2R5Pgo8L2h0bWw+Cg==

--frontier--

~~~

Cada parte consiste en su propio encabezado de contenido y un cuerpo. 
### **Subtipos Multipart**
El estándar MIME define varios subtipos de mensajes multipart. El subtipo se especifica en el encabezado "Content-Type" del mensaje general.

La siguiente es una lista de los subtipos más comúnmente utilizados.

- Mezclado: Multipart/mixed se utiliza para enviar archivos con diferentes encabezados de "Content-Type" en línea. Si se envían imágenes u otros archivos fácilmente legibles, la mayoría de los clientes de correo los mostrarán en línea.
- Mensaje: Una parte de mensaje contiene un mensaje de correo electrónico.
- Digest: el digest es una forma simple de enviar múltiples mensajes de texto. El tipo de contenido predeterminado para cada parte es "message/rfc822".
- Alternativa: El subtipo alternativo indica que cada parte es una versión "alternativa" del mismo contenido (o similar), cada una en un formato diferente denotado por su encabezado "Content-Type".

El multipart/alternative se utiliza comúnmente para correos electrónicos con dos partes, una de texto plano (text/plain) y una HTML (text/html). La parte de texto plano proporciona compatibilidad hacia atrás, mientras que la parte HTML permite el uso de formato y hipervínculos. La mayoría de los clientes de correo electrónico ofrecen una opción al usuario para preferir texto plano sobre HTML; este es un ejemplo de cómo los factores locales pueden afectar cómo una aplicación elige qué parte "mejor" del mensaje mostrar. 

{{% alert color="primary" %}} 

Para más información, siga estos enlaces a los archivos de RFC.

- [RFC2045](https://www.rfc-archive.org/getrfc.php?rfc=2045#gsc.tab=0)
- [RFC131](https://www.rfc-archive.org/getrfc.php?rfc=131#gsc.tab=0)

{{% /alert %}}