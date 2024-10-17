---
title: "Configuración de la codificación de texto predeterminada en el mensaje de correo electrónico"
url: /es/net/configuracion-de-la-codificacion-de-texto-predeterminada-en-el-mensaje-de-correo-electronico/
weight: 120
type: docs
---


Este artículo presenta la propiedad [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) y explica cómo se usa. Usando esta propiedad, puedes establecer la codificación de texto predeterminada para las siguientes propiedades:

- De: Nombre para mostrar
- Para: Nombre para mostrar
- Asunto
- Cuerpo
## **Configuración de la codificación de texto predeterminada**
En versiones anteriores de Aspose.Email, la codificación de texto para las propiedades de de, para, asunto y cuerpo se configuraba por separado. Para mejorar la usabilidad, añadimos la propiedad [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) que establece todas a la vez. Ahora es más fácil asegurarse de que todo el texto en las propiedades anteriores esté codificado correctamente en el mensaje de correo electrónico. El siguiente fragmento de código te muestra cómo usar una palabra en francés como nombre para mostrar para direcciones de correo electrónico, asunto y cuerpo.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}