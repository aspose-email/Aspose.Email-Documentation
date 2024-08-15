---
title: "Extraer el contenido de los mensajes de los correos electrónicos"
url: /es/net/extracting-message-contents-from-emails/
weight: 30
type: docs
---

# Extraer el contenido de los mensajes de los correos electrónicos

## **Mostrar información de correo electrónico en la pantalla**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades de los mensajes de correo electrónico. La información del encabezado (que se explica en [Extracción de encabezados de correo electrónico](https://docs.aspose.com/email/es/net/extracting-message-contents-from-emails/#extracting-email-headers)) pueden extraerse y manipularse de diferentes maneras. En este artículo se explica cómo mostrar la información del encabezado del correo electrónico seleccionado y el cuerpo del correo electrónico en la pantalla. Para mostrar la información del correo electrónico en la pantalla, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Cargue un mensaje de correo electrónico en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Muestra el contenido del correo electrónico en la pantalla.

El siguiente fragmento de código muestra cómo mostrar la información del correo electrónico en la pantalla.

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

## **Extracción de encabezados de correo electrónico**

El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y RFC que se incluye en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Los tipos de encabezados más comunes se definen en [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/) clase. Es una clase sellada que funciona como una enumeración normal. Para extraer los encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Cargue un mensaje de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Una vez que se haya cargado un mensaje de correo electrónico, obtendremos su contenido sin procesar.

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) la clase en sí contiene propiedades como From, To, Cc, Subject, etc. Estas propiedades se pueden extraer de los encabezados.

El siguiente fragmento de código muestra cómo extraer los encabezados de los correos electrónicos.

## **Obtener valores de encabezado decodificados**

El siguiente fragmento de código muestra cómo obtener valores de encabezado decodificados.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Obtenga el cuerpo del texto sin formato**

The [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) La propiedad devuelve una representación en texto plano del cuerpo de un mensaje.

```csharp
string plainTextBody = mailMessage.Body;
```

Nota: Si la parte MIME texto/simple está presente en un mensaje, la propiedad devuelve sus datos de texto. De lo contrario, devuelve el contenido de texto separado del [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) propiedad sin marcado html.

## **Obtener el cuerpo del HTML como texto sin formato**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase proporciona la función para extraer el cuerpo HTML del mensaje como texto sin formato. El [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) la clase proporciona una [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) método que devuelve el cuerpo HTML en texto plano. Este método analiza el [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) propiedad y devuelve contenido de texto plano separado ignorando el marcado html. El [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) El método acepta un parámetro booleano que indica si el cuerpo debe contener URL o no. Si se pasa el parámetro como verdadero, se indica que el cuerpo del HTML debe contener direcciones URL.

El siguiente fragmento de código demuestra el uso de [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) método para extraer el cuerpo HTML del correo electrónico como texto sin formato.

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
