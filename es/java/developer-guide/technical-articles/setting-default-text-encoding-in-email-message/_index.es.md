---
title: "Configuración de la codificación de texto predeterminada en un mensaje de correo electrónico"
url: /es/java/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


Este artículo presenta la [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) propiedad y explica cómo se usa. Con esta propiedad, puede establecer la codificación de texto predeterminada para las siguientes propiedades:

- De: Nombre para mostrar
- Para: Mostrar nombre
- Subject
- Body
## **Configuración de la codificación de texto predeterminada**
En las versiones anteriores de Aspose.Email, la codificación del texto para las propiedades de origen, destino, asunto y cuerpo se establecía por separado. Para mejorar la usabilidad, hemos añadido el [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) propiedad que establece todo a la vez. Ahora es más fácil garantizar que todo el texto de las propiedades anteriores esté codificado correctamente en el mensaje de correo electrónico. En el siguiente fragmento de código, se muestra cómo usar una palabra en francés como nombre para mostrar en las direcciones de correo electrónico, el asunto y el cuerpo.



~~~Java
// Create an instance of MailMessage
String fileName = "data/";
MailMessage msg = new MailMessage();

// Set the default or preferred encoding. This encoding will be used as the default for the from/to email addresses, subject and body of message.
msg.setPreferredTextEncoding(Charset.forName("cp1252"));

// Set email addresses, subject and body
msg.setFrom(new MailAddress("dmo@domain.com", "démo"));
msg.getTo().addItem(new MailAddress("dmo@domain.com", "démo"));
msg.setSubject("démo");
msg.setHtmlBody("démo");
msg.save(fileName + "SetDefaultTextEncoding_out.msg", SaveOptions.getDefaultMsg());
~~~