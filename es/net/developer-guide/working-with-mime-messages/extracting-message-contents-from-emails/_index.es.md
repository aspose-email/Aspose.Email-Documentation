---
title: "Extrayendo Contenidos de Mensajes de Correos Electrónicos"
url: /es/net/extracting-message-contents-from-emails/
weight: 30
type: docs
---

# Extrayendo Contenidos de Mensajes de Correos Electrónicos

## **Mostrando Información del Correo Electrónico en Pantalla**

El [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información de encabezado (discutida en [Extrayendo Encabezados de Correo Electrónico](https://docs.aspose.com/email/es/net/extracting-message-contents-from-emails/#extracting-email-headers)) se puede extraer y manipular de diferentes maneras. Este artículo explica cómo mostrar información seleccionada del encabezado del correo electrónico y el cuerpo del correo en pantalla. Para mostrar información del correo electrónico en pantalla, sigue estos pasos:

- Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Carga un mensaje de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Muestra el contenido del correo en la pantalla.

El siguiente fragmento de código te muestra cómo mostrar información del correo electrónico en la pantalla.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

// Create MailMessage instance by loading an Eml file
MailMessage message = MailMessage.Load(dataDir + "test.eml", new EmlLoadOptions());

// Gets the sender info, recipient info, Subject, htmlbody and textbody
Console.Write("From:");
Console.WriteLine(message.From);
Console.Write("To:");
Console.WriteLine(message.To);
Console.Write("Subject:");
Console.WriteLine(message.Subject);
Console.WriteLine("HtmlBody:");
Console.WriteLine(message.HtmlBody);
Console.WriteLine("TextBody");
Console.WriteLine(message.Body);
```

## **Extrayendo Encabezados de Correo Electrónico**

El encabezado de un correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y por la RFC incluido en los mensajes de correo electrónico de Internet. Un encabezado de correo electrónico se puede especificar utilizando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Los tipos de encabezado comunes están definidos en la clase [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). Es una clase sellada que funciona como una enumeración normal. Para extraer encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Carga un mensaje de correo electrónico en la instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Después de que se haya cargado un mensaje de correo electrónico, obtendremos su contenido en bruto.

La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) en sí misma contiene propiedades como De, Para, Cc, Asunto, etc. Estas propiedades se pueden extraer de los encabezados.

El siguiente fragmento de código te muestra cómo extraer encabezados de correo electrónico.

## **Obtener Valores de Encabezado Decodificados**

El siguiente fragmento de código te muestra cómo obtener valores de encabezado decodificados.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Obtener Cuerpo de Texto Plano**

La propiedad [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) devuelve una representación en texto plano del cuerpo de un mensaje.

```csharp
string plainTextBody = mailMessage.Body;
```

Nota: Si la parte MIME de texto/plano está presente en un mensaje, la propiedad devuelve sus datos de texto. De lo contrario, devuelve el contenido de texto separado de la propiedad [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) sin marcado html.

## **Obtener Cuerpo HTML como Texto Plano**

La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) proporciona la función para extraer el cuerpo HTML del mensaje como texto plano. La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) proporciona un método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) que devuelve el cuerpo HTML en texto plano. Este método analiza la propiedad [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) y devuelve contenido de texto plano separado ignorando el marcado html. El método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) acepta un parámetro booleano que indica si el cuerpo debe contener URLs o no. Pasar el parámetro como verdadero indica que el cuerpo HTML debe contener URLs.

El siguiente fragmento de código demuestra el uso del método [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) para extraer el cuerpo HTML del correo electrónico como texto plano.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

MailMessage mail = MailMessage.Load(dataDir + "HtmlWithUrlSample.eml");

string body_with_url = mail.GetHtmlBodyText(true);// body will contain URL
string body_without_url = mail.GetHtmlBodyText(false);// body will not contain URL

Console.WriteLine("Body with URL: " + body_with_url);
Console.WriteLine("Body without URL: " + body_without_url);
```