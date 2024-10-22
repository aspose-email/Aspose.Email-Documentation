---
title: "Creando y Configurando Contenidos de Correos Electrónicos en C++ y Enviando Correos Electrónicos usando SmtpClient"
description: "Para crear y configurar contenidos de correos electrónicos en C++, utiliza la clase MailMessage que puede crear y guardar el mensaje de correo en diferentes formatos como EML, MSG y MHTML."
url: /es/cpp/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Creando y configurando contenidos de correos electrónicos"
keywords: "c++ enviar correo electrónico"
---

## **Crear Nuevo Mensaje de Correo Electrónico**
La clase MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores crear un nuevo mensaje de correo electrónico. Propiedades básicas del correo electrónico como De, Para, Asunto y cuerpo pueden ser fácilmente adjuntadas al mensaje de correo recién creado. Igualmente, podemos guardar el mensaje de correo en diferentes formatos como EML, MSG y MHTML.

<a name="csharp-create-new-email-msg" id="csharp-create-new-email-msg"><strong>Pasos: Crear Nuevo Mensaje de Correo Electrónico en C#</strong></a>

- Crear una instancia de la clase MailMessage.
- Configurar las propiedades del mensaje de correo.
- Guardar el mensaje de correo en diferentes formatos.
- Crear una instancia de la clase SmtpClient y enviar el correo electrónico usando el método Send.

El siguiente fragmento de código C++ te muestra cómo crear un nuevo correo electrónico con diferentes propiedades.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CreateNewMailMessage-CreateNewMailMessage.cpp" >}}

## **Cambiando direcciones de correo electrónico a un nombre amigable**
Los ejemplos de programación a continuación demuestran cómo cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo electrónico. Un nombre amigable es un nombre que es más comprensible para los humanos que la dirección de correo electrónico, por ejemplo, John Smith en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre amigable con una dirección de correo electrónico en el constructor de la clase MailMessage.

Para cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo electrónico, sigue estos pasos:

- Crear una instancia de la clase MailMessage y especificar direcciones de correo electrónico en los campos **Para** y **De** junto con nombres amigables.
- Especificar las direcciones de correo electrónico Cc y Bcc junto con nombres amigables llamando al constructor de la clase MailMessage en la instancia de MailMessage.
- Crear una instancia de la clase SmtpClient y enviar el correo electrónico usando el método Send.

El siguiente fragmento de código te muestra cómo mostrar nombres para direcciones de correo electrónico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ChangeEmailAddress-ChangeEmailAddress.cpp" >}}

## **Configurar el Cuerpo del Correo**
La clase MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que son transmitidos a un servidor SMTP para entrega usando la clase SmtpClient. Se puede especificar un cuerpo de correo utilizando la clase MailMessage. Un correo electrónico puede tener múltiples cuerpos. Hay dos tipos de cuerpos de correo en la clase MailMessage:

- Cuerpo HTML
- Cuerpo de texto

Además de HtmlBody y TextBody, Aspose.Email tiene otras dos propiedades de solo lectura relacionadas con el cuerpo del correo:

- IsBodyText: indica al usuario si el cuerpo es texto.
- IsBodyHtml: indica al usuario si el cuerpo es HTML o texto plano.

Este artículo muestra cómo definir texto de cuerpo de texto plano o HTML, configurar texto alternativo y codificar el cuerpo del correo.

### **Configurar Cuerpo HTML**
[HtmlBody](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) se usa para especificar el contenido HTML de un cuerpo de mensaje. HtmlBody debe estar encerrado entre las etiquetas <html> </html>. El siguiente fragmento de código te muestra cómo establecer el cuerpo HTML.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetHTMLBody-SetHTMLBody.cpp" >}}

### **Configurar Texto Alternativo**
Usa la clase AlternateView para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envías un mensaje en HTML, también podrías querer proporcionar una versión en texto plano en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no pueden mostrar contenido HTML. Esta clase tiene dos propiedades, LinkedResources y BaseUri, que se utilizan para resolver URL dentro del contenido del correo electrónico.

- LinkedResources es una colección de objetos LinkedResources. Cuando se renderiza, las URL dentro del contenido del correo electrónico se comparan primero con las URL en el Enlace de Contenido de cada objeto LinkedResources en la colección LinkedResources, y se resuelven.
- BaseUri es utilizada por el lector de correo para resolver URL relativas dentro del cuerpo, y también para resolver URL relativas de Enlace de Contenido, en la colección LinkedResources.

El siguiente fragmento de código C++ te muestra cómo establecer texto alternativo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetAlternateText-SetAlternateText.cpp" >}}