---
title: "Establecer la Codificación de Texto Predeterminada en el Mensaje de Correo Electrónico"
url: /es/java/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


Este artículo presenta la propiedad [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) y explica cómo se utiliza. Usando esta propiedad, puedes establecer la codificación de texto predeterminada para las siguientes propiedades:

- De: Nombre para mostrar
- Para: Nombre para mostrar
- Asunto
- Cuerpo
## **Establecer la Codificación de Texto Predeterminada**
En versiones anteriores de Aspose.Email, la codificación de texto para las propiedades de de, para, asunto y cuerpo se establecía por separado. Para mejorar la usabilidad, añadimos la propiedad [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) que establece todo a la vez. Ahora es más fácil asegurar que todo el texto en las propiedades anteriores esté codificado correctamente en el mensaje de correo electrónico. El siguiente fragmento de código te muestra cómo usar una palabra francesa como nombre para mostrar en direcciones de correo electrónico, asunto y cuerpo.



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