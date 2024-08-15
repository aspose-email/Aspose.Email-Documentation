---
title: "Creación y configuración del contenido de los correos electrónicos en.NET"
url: /es/net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Creación y configuración del contenido de los correos electrónicos"
---

## **Crear nuevo mensaje de correo electrónico**

Para crear un nuevo mensaje de correo electrónico, puede usar [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. El **MailMessage** La clase también inicializa las propiedades del mensaje de correo electrónico creado, como la dirección de correo electrónico del remitente, las direcciones de correo electrónico de los destinatarios, el asunto del correo electrónico y el contenido del cuerpo del correo electrónico en formato HTML.

Tenga en cuenta el siguiente código, con pasos detallados, para crear un nuevo mensaje de correo electrónico y establecer sus propiedades.

**Pasos de código:**

1. Cree una nueva instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Configure el [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) propiedad de la dirección de correo electrónico del remitente.
3. Configure el [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) propiedad de una lista separada por comas de las direcciones de correo electrónico de los destinatarios.
4. Configure el [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) propiedad al asunto del correo electrónico.
5. Configure el [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) propiedad del contenido HTML del cuerpo del correo electrónico.

**Ejemplo de código:**
```cs
// Create a new instance of MailMessage class
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "New message",
    HtmlBody = @"<!DOCTYPE html>
    <html>
     <head>
      <style>
       h3{font-family:Verdana, sans-serif;color:#000000;background-color:#ffffff;}
       p {font-family:Verdana, sans-serif;font-size:14px;font-style:normal;
         font-weight:normal;color:#000000;background-color:#ffffff;}
      </style>
     </head>
     <body>
       <h3>New message</h3>
       <p>This is a new message created by Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Especificación de varios destinatarios**

Hay tres maneras de especificar los destinatarios de un mensaje de correo electrónico: mediante **To**, **CC**, o **BCC** fields.

- **To** El campo es el destinatario principal de tu mensaje. Puede introducir una o más direcciones de correo electrónico en este campo, separadas por comas. El campo Para es obligatorio para todos los mensajes de correo electrónico.

- **CC** field son las siglas de Carbon Copy. Se usa para enviar una copia de su mensaje a otras personas interesadas o involucradas en el tema. El campo CC es opcional y también puede contener varias direcciones de correo electrónico. Los destinatarios del campo CC pueden ver quién más ha recibido el mensaje.

- **BCC** field son las siglas de Blind Carbon Copy. Es similar al campo CC, pero los destinatarios del campo BCC están ocultos para los demás destinatarios. El campo BCC es útil cuando quieres proteger la privacidad de algunos destinatarios o evitar que su bandeja de entrada se llene de respuestas. El campo BCC también es opcional y puede tener varias direcciones de correo electrónico.

Tenga en cuenta el siguiente código, con pasos detallados, para especificar varios destinatarios para un mensaje de correo electrónico.

**Pasos de código:**

1. Cree una nueva instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Configure el [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) propiedad de la dirección de correo electrónico del remitente.
3. Configure el [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) propiedad de una matriz de direcciones de correo electrónico de los destinatarios principales.
4. Configure el [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) propiedad de una serie de direcciones de correo electrónico de los destinatarios que recibirán una copia del correo electrónico.
5. Configure el [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) propiedad de una serie de direcciones de correo electrónico de los destinatarios que recibirán una copia ciega del correo electrónico.

**Ejemplo de código:**

```cs
var eml = new MailMessage
{
    // Specify From address
    From = "sender@sender.com",
    //  Specify recipients’ mail addresses
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Specify CC addresses
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Specify BCC addresses
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Añadir nombres para mostrar a las direcciones de correo electrónico**

Junto con una dirección de correo electrónico, un **nombre para mostrar** se puede incluir para identificar al remitente o al destinatario del correo electrónico. Puede incluir el nombre completo, el apodo u otro identificador de una persona.

Cuando se muestra un mensaje de correo electrónico en un cliente de correo electrónico o en una interfaz de correo web, el nombre mostrado normalmente se muestra junto a la dirección de correo electrónico, lo que facilita al usuario identificar de quién proviene el mensaje o a quién va dirigido. Por ejemplo, una dirección de correo electrónico puede ser \"johndoe@example.com», pero el nombre para mostrar asociado a ella puede ser «John Doe».

Para agregar nombres para mostrar a las direcciones de correo electrónico de un mensaje de correo electrónico, ten en cuenta el siguiente código con pasos detallados:

**Pasos de código:**

1. Cargue el mensaje de correo electrónico desde un archivo mediante [MailMessage.Load]() method.
2. Configura el remitente del correo electrónico mediante el [From]() propiedad del objeto eml mediante la creación de un nuevo [MailAddress]() objeto con la dirección de correo electrónico y el nombre para mostrar del remitente.
3. Agregue un destinatario al correo electrónico mediante el [To]() propiedad del objeto eml; si es necesario, añada la lista CC (Carbon Copy) utilizando el [CC]() propiedad, lista BCC (Blind Carbon Copy) utilizando el [Bcc]() propiedad y llame al [Add]() método con un nuevo [MailAddress]() objeto que contiene la dirección de correo electrónico y un nombre para mostrar del destinatario.

**Ejemplo de código:**

```cs
// Load eml from file
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// A To address with a friendly name can also be specified like this
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Specify Cc and Bcc email address along with a friendly name
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Guangzhou Team"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Mostrar los asistentes opcionales en la salida del encabezado mht**

El ejemplo de código que aparece a continuación demuestra cómo usar *mostrar asistentes opcionales* función al guardar un mensaje en formato mhtml:


```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

//if you need to skip OptionalAttendees in mhtml file you can clear format template for OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```


## **Establecer el cuerpo del correo**

En este artículo aprenderás cómo:

- [establecer cuerpo de texto sin formato](#Set-Plain-Text-Body)
- [establecer cuerpo HTML](#Setting-HTML-Body)
- [establecer texto alternativo](#Setting-Alternate-Text)
- [especificar la codificación del cuerpo del correo](#Specifying-Mail-Body-Encoding)

### **Configuración del cuerpo de texto sin formato**

Se puede especificar el cuerpo de un correo mediante el [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    Body = "This is a texto plano body"
};
```

### **Configuración del cuerpo HTML**

El cuerpo de un correo también se puede especificar mediante [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    HtmlBody = "<html><body>This is the HTML body</body></html>"
};
```

### **Configuración de texto alternativo**

Una vista alternativa en un archivo EML es una representación adicional del contenido del correo electrónico que se puede usar para proporcionar una representación diferente del mensaje de correo electrónico. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar un **texto plano** versión en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no puedan mostrar contenido HTML. Para ello, utilice el [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) clase. Esta clase tiene dos propiedades, [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) and [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), que se utilizan para resolver las URL incluidas en el contenido del correo electrónico.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) es una colección de [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) objetos. Cuando se representan, las URL del contenido del correo electrónico se comparan primero con las URL del enlace de contenido de cada uno [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) objeto en el [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) recogida y resuelta.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) lo utiliza el lector de correo para resolver las URL relativas dentro del cuerpo y también para resolver las URL de enlaces de contenido relativas, en el [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) collection.

Considera el siguiente código con pasos detallados para establecer un texto alternativo.

**Pasos de código:**

1. Crea una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Create [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) para ver un mensaje de correo electrónico con el contenido especificado en la cadena.
3. Añadir texto alternativo mediante [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) método de [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/) collection.

**Ejemplo de código:**
```cs
// Declare message as MailMessage instance
var eml = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");

// Adding alternate text
 eml.AlternateViews.Add(alternate);
```

### **Especificación de la codificación del cuerpo del correo**

Aspose.Email usa el [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase para especificar la codificación del cuerpo del correo electrónico. Por ejemplo:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Configuración de propiedades adicionales de MailMessage**

Con Aspose.Email puedes usar propiedades adicionales del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase como:

- [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) propiedad - conjuntos **fecha y hora** de un correo electrónico. De forma predeterminada, la fecha es la fecha real en la que se envió el mensaje y la hora es la hora en que se envió, tal y como muestra Microsoft Outlook. Sin embargo, la hora real de entrega del correo electrónico la añade el propio servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, donde [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) establece el campo Fecha.

   ```cs
   // For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
  
   // Add by SMTP server in delivery emails
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
  
   // Add by SMTP server in delivery emails
   Return-Path: <xyz@oikoscucine.it>
  
   // Add by SMTP server in delivery emails
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: For ABC
  
   // Date will set the Date field, outlook will show this as
   Date: Thu, 22 Feb 2007 20:58:51 +0300
   Message-ID: <01c756c4$41b554d0$6c822ecf@dishonestyinsufferably>
   MIME-Version: 1.0
   Content-Type: multipart/alternative;
   boundary="----=_NextPart_000_0006_01C7569A.58DF4CD0"
   X-Mailer: Microsoft Office Outlook, Build 11.0.5510
   X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2800.1106
   Thread-Index: Aca6Q:=ES0M(9-=(<.<1.<Q9@QE6CD==
   X-Read: 1
   ```

- [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) enumeración: especifica los niveles de prioridad para enviar un mensaje de correo electrónico. Puede ser baja, normal o alta. La prioridad influye en la velocidad de transmisión y en la entrega.
- [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) enumeración: especifica cinco niveles de sensibilidad.
- [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/)- especifica el software que creó el mensaje de correo electrónico.

El siguiente fragmento de código ilustra cómo se puede usar cada una de las propiedades descritas anteriormente.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Solicitud de un acuse de recibo de lectura**

Para solicitar un [leer recibo](https://en.wikipedia.org/wiki/Return_receipt), usa Aspose.Email [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) propiedad del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Esta propiedad contiene los valores de [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration) enumeration.

Tenga en cuenta lo siguiente **ejemplo de código**:

```cs
// Create an Instance of MailMessage class
var eml = new MailMessage
{
    // Specify From, To, HtmlBody, DeliveryNotificationOptions field
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>This is the Html body</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Crea una instancia de SmtpClient Class
var client = new SmtpClient
{
    // Specify your mailing host server, Username, Password and Port No
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};

try
{
    // Client.Send will send this message
    client.Send(eml);
    // Display ‘Message Sent’, only if message sent successfully
    Console.WriteLine(@"Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Note**: Es posible que las solicitudes de acuse de recibo de lectura no siempre se cumplan porque:

- Es posible que un cliente de correo no implemente esa funcionalidad.
- Es posible que el usuario final tenga desactivada esa funcionalidad.
- El usuario final puede optar por no enviar uno.


## **Establecer encabezados de correo electrónico**

Los encabezados de correo electrónico representan un estándar de Internet y el RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Los tipos de encabezados más comunes se definen en [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/) clase. Es una clase sellada que funciona como una enumeración normal.

Normalmente, el encabezado de un correo electrónico contiene los siguientes campos:

- **To**: Las direcciones de los destinatarios se pueden especificar en el campo Para. Los destinatarios del campo Para son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- **From**: Este campo presenta la dirección de correo electrónico del remitente del mensaje.
- **Cc**: Permite a los usuarios enviar un mensaje como «copia exacta» o «copia de cortesía». Es decir, no se espera que el receptor responda o actúe. Por lo general, el personal de supervisión recibe una notificación mediante un CC.
- **Bcc**: Son las siglas de Blind Carbon Copy, que le permite enviar un correo electrónico a un destinatario que está oculto para otros destinatarios.
- **ReplyTo**: Este campo de encabezado está destinado a indicar a dónde quiere que vayan las respuestas el remitente.
- **Subject**: Título, encabezamiento, asunto. Se utiliza a menudo como indicador de hilo para los mensajes que responden o comentan otros mensajes.
- **Date**: Este encabezado especifica una fecha (y una hora). Normalmente es la fecha en la que se redactó y envió el mensaje.
- **XMailer**: Información sobre el software cliente del originador. Ejemplo: X-Mailer: Aspose.Email. Los clientes de correo utilizan XMailer. Los distintos clientes de correo tendrán diferentes valores de XMailer. El valor de XMailer de MS Outlook es Microsoft Office Outlook, versión 11.0.5510. El receptor o el lector de correo electrónico lo ignoran.

Normalmente, el encabezado de un correo electrónico tiene un aspecto similar al siguiente:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Para personalizar el encabezado de un correo electrónico, sigue estas instrucciones **pasos de código**:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Especifique To, From, Cc, Bcc, Reply To, Subject, Date y XMailer mediante una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Crea una instancia del [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) clase y especifique el encabezado personalizado.
- Añada el encabezado personalizado a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

Los siguientes **fragmento de código** muestra cómo configurar los encabezados de los correos electrónicos.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "test mail",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

El fragmento de código anterior produce un encabezado de correo electrónico con el siguiente formato:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Insertar un encabezado en una ubicación específica**

The [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) método del [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) class inserta un encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) el método no será de ayuda. Para lograr esto, usa el [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) método del [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes que otros encabezados con el mismo nombre. El siguiente fragmento de código muestra cómo insertar un encabezado en una ubicación específica.

```cs
eml.Headers.Insert("Received", "Value");
```

### **Guardar todos los encabezados en MHTML**

The [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) propiedad del [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) La clase define si es necesario guardar todos los encabezados en la salida mhtml o no. El siguiente fragmento de código muestra cómo guardar todos los encabezados de un archivo mhtml:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Agregar encabezados personalizados al correo electrónico**

Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Para especificar un **encabezado personalizado** en un mensaje de correo electrónico, considere el siguiente ejemplo de código:

```cs
eml.Headers.Add("secret-header", "mystery");
```

El fragmento de código anterior produce un encabezado de correo electrónico con el siguiente formato:

```cs
secret-header: mystery
```

## **Guardar un archivo HTML con campos de tareas en un encabezado**

The [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) la enumeración le permite especificar que los campos de tareas deben incluirse en el encabezado del archivo HTML guardado. El siguiente fragmento de código muestra cómo conservar los campos de tareas en un encabezado al guardar un archivo HTML:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Firma correos electrónicos con DKIM**

> **_NOTE:_** La función solo está disponible para las versiones de biblioteca orientadas a .NET Framework. Las versiones dirigidas a .NET Core no tienen esta función.

Aspose.Email permite firmar correos electrónicos con DKIM (DomainKeys Identified Mail). Esto permite a una organización asumir la responsabilidad de un mensaje que está en tránsito ([Más información](https://www.dkim.org/)). DKIM añade una firma digital a los encabezados de los mensajes de correo electrónico que los destinatarios pueden validar. La clave pública del remitente permite al receptor verificar que la firma coincide con el contenido del mensaje. La [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase se usa para establecer la información criptográfica y de firma para firmar el mensaje. El siguiente fragmento de código muestra cómo firmar correos electrónicos con DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```
