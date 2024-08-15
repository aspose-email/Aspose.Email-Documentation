---
title: "Configuración de la codificación de texto predeterminada en un mensaje de correo electrónico"
url: /es/net/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


Este artículo presenta la [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) propiedad y explica cómo se usa. Con esta propiedad, puede establecer la codificación de texto predeterminada para las siguientes propiedades:

- De: Nombre para mostrar
- Para: Mostrar nombre
- Subject
- Body
## **Configuración de la codificación de texto predeterminada**
En las versiones anteriores de Aspose.Email, la codificación del texto para las propiedades de origen, destino, asunto y cuerpo se establecía por separado. Para mejorar la usabilidad, hemos añadido el [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) propiedad que establece todo a la vez. Ahora es más fácil garantizar que todo el texto de las propiedades anteriores esté codificado correctamente en el mensaje de correo electrónico. En el siguiente fragmento de código, se muestra cómo usar una palabra en francés como nombre para mostrar en las direcciones de correo electrónico, el asunto y el cuerpo.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}
