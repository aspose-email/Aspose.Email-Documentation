---
title: "Creación y configuración del contenido de los correos electrónicos en C++ y envío de correos electrónicos mediante SMTPClient"
description: "Para crear y configurar el contenido del correo electrónico en C++, use la clase MailMessage que puede crear y guardar el mensaje de correo en diferentes formatos como EML, MSG y MHTML."
url: /es/cpp/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Creación y configuración del contenido de los correos electrónicos"
keywords: "c++ enviar correo electrónico"
---

## **Crear nuevo mensaje de correo electrónico**
La clase MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores crear un nuevo mensaje de correo electrónico. Las propiedades básicas del correo electrónico, como De, Para, Asunto y cuerpo, se pueden adjuntar fácilmente al mensaje de correo recién creado. Del mismo modo, podemos guardar el mensaje de correo en diferentes formatos, como EML, MSG y MHTML.

<a name="csharp-create-new-email-msg" id="csharp-create-new-email-msg"><strong>Pasos: crear un nuevo mensaje de correo electrónico en C#</strong></a>

- Crea una instancia de la clase MailMessage.
- Establezca las propiedades de los mensajes de correo.
- Guarda el mensaje de correo en diferentes formatos.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código de C++ muestra cómo crear un nuevo correo electrónico con diferentes propiedades.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CreateNewMailMessage-CreateNewMailMessage.cpp" >}}

## **Cambiar las direcciones de correo electrónico por un nombre descriptivo**
Los siguientes ejemplos de programación muestran cómo cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico. Un nombre descriptivo es un nombre que es más fácil de entender para los humanos que la dirección de correo electrónico, por ejemplo, John Smith en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre descriptivo a una dirección de correo electrónico en el constructor de la clase MailMessage.

Para cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico, sigue estos pasos:

- Cree una instancia de la clase MailMessage y especifique las direcciones de correo electrónico en **To** and **From** campos junto con nombres descriptivos.
- Especifique las direcciones de correo electrónico Cc y Bcc junto con nombres descriptivos llamando al constructor de la clase MailMessage en la instancia de MailMessage.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo mostrar los nombres de las direcciones de correo electrónico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ChangeEmailAddress-ChangeEmailAddress.cpp" >}}

## **Establecer el cuerpo del correo**
La clase MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante la clase SmtpClient. El cuerpo de un correo se puede especificar mediante la clase MailMessage. Un correo electrónico puede tener varios cuerpos. Hay dos tipos de cuerpos de correo en la clase MailMessage:

- Cuerpo HTML
- Cuerpo del texto

Además de HTMLBody y TextBody, Aspose.Email tiene otras dos propiedades de solo lectura relacionadas con el cuerpo del correo:

- isBodyText: indica al usuario si el cuerpo es texto.
- isBodyHtml: indica al usuario si el cuerpo es HTML o texto sin formato.

En este artículo se muestra cómo definir texto sin formato o texto principal HTML, establecer texto alternativo y codificar el cuerpo del correo electrónico.

### **Configuración del cuerpo HTML**
[HtmlBody](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) se usa para especificar el contenido HTML del cuerpo de un mensaje. HTMLBody debe estar entre <html> </html> etiquetas. El siguiente fragmento de código muestra cómo configurar el cuerpo del HTML.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetHTMLBody-SetHTMLBody.cpp" >}}

### **Configuración de texto alternativo**
Utilice la clase AlternateView para especificar copias de un mensaje de correo electrónico en un formato diferente. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no puedan mostrar contenido HTML. Esta clase tiene dos propiedades, linkedResources y baseURI, que se utilizan para resolver las URL incluidas en el contenido del correo electrónico.

- LinkedResources es una colección de objetos LinkedResources. Cuando se representan, las URL del contenido del correo electrónico se comparan primero con las URL del enlace de contenido de cada objeto de LinkedResources de la colección LinkedResources y se resuelven.
- El lector de correo utiliza BaseURI para resolver las URL relativas dentro del cuerpo y también para resolver las URL de enlaces de contenido relativas de la colección LinkedResources.

El siguiente fragmento de código de C++ muestra cómo configurar texto alternativo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetAlternateText-SetAlternateText.cpp" >}}
