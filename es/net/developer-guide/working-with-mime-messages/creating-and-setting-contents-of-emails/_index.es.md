---
title: "Creación y configuración de contenidos de correos electrónicos en .NET"
url: /es/net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Creación y configuración de contenidos de correos electrónicos"
---

## **Crear nuevo mensaje de correo electrónico**

Para crear un nuevo mensaje de correo electrónico, puedes usar la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). La clase **MailMessage** también inicializa propiedades del mensaje de correo electrónico creado, como la dirección de correo electrónico del remitente, las direcciones de correo electrónico de los destinatarios, el asunto del correo electrónico y el contenido del cuerpo del correo electrónico en formato HTML.

Considera el siguiente código, con pasos detallados, para crear un nuevo mensaje de correo electrónico y establecer sus propiedades.

**Pasos de código:**

1. Crea una nueva instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Establece la propiedad [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) a la dirección de correo electrónico del remitente.
3. Establece la propiedad [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) a una lista de direcciones de correo electrónico de los destinatarios, separadas por comas.
4. Establece la propiedad [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) al asunto del correo electrónico.
5. Establece la propiedad [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) al contenido HTML del cuerpo del correo electrónico.

**Ejemplo de código:**
```cs
// Crea una nueva instancia de la clase MailMessage
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Nuevo mensaje",
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
       <h3>Nuevo mensaje</h3>
       <p>Este es un nuevo mensaje creado por Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Especificando múltiples destinatarios**

Hay tres formas de especificar destinatarios de un mensaje de correo electrónico: usando los campos **To**, **CC** o **BCC**.

- El campo **To** es el destinatario principal de tu mensaje. Puedes ingresar una o más direcciones de correo electrónico en este campo, separadas por comas. El campo To es obligatorio para cada mensaje de correo electrónico.

- El campo **CC** significa copia de carbón. Se utiliza para enviar una copia de tu mensaje a otras personas que están interesadas o involucradas en el tema. El campo CC es opcional y también puede contener múltiples direcciones de correo electrónico. Los destinatarios en el campo CC pueden ver quién más recibió el mensaje.

- El campo **BCC** significa copia de carbón oculta. Es similar al campo CC, pero los destinatarios en el campo BCC están ocultos de los otros destinatarios. El campo BCC es útil cuando deseas proteger la privacidad de algunos destinatarios o evitar llenar sus bandejas de entrada con respuestas. El campo BCC también es opcional y puede tener múltiples direcciones de correo electrónico.

Considera el siguiente código, con pasos detallados, para especificar múltiples destinatarios para un mensaje de correo electrónico.

**Pasos de código:**

1. Crea una nueva instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Establece la propiedad [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) a la dirección de correo electrónico del remitente.
3. Establece la propiedad [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) a un arreglo de direcciones de correo electrónico de los destinatarios principales.
4. Establece la propiedad [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) a un arreglo de direcciones de correo electrónico de los destinatarios que recibirán una copia del correo electrónico.
5. Establece la propiedad [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) a un arreglo de direcciones de correo electrónico de los destinatarios que recibirán una copia de carbón oculta del correo electrónico.

**Ejemplo de código:**

```cs
var eml = new MailMessage
{
    // Especifica la dirección From
    From = "sender@sender.com",
    // Especifica las direcciones de correo de los destinatarios
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Especifica las direcciones CC
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Especifica las direcciones BCC
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Agregar nombres de visualización a las direcciones de correo electrónico**

Junto con una dirección de correo electrónico, se puede incluir un **nombre de visualización** para identificar al remitente o destinatario del correo electrónico. Puede incluir el nombre completo de una persona, apodo u otro identificador.

Cuando un mensaje de correo electrónico se muestra en un cliente de correo electrónico o en una interfaz de webmail, el nombre de visualización generalmente se muestra junto a la dirección de correo electrónico, facilitando al usuario identificar de quién es el mensaje o a quién va dirigido. Por ejemplo, una dirección de correo electrónico podría ser "johndoe@example.com", pero el nombre de visualización asociado podría ser "John Doe".

Para agregar nombres de visualización a las direcciones de correo electrónico en un mensaje de correo electrónico, considera el siguiente código con pasos detallados:

**Pasos de código:**

1. Carga el mensaje de correo electrónico desde un archivo usando el método [MailMessage.Load]() .
2. Establece el remitente del correo electrónico usando la propiedad [From]() del objeto eml creando un nuevo objeto [MailAddress]() con la dirección de correo electrónico y un nombre de visualización del remitente.
3. Agrega un destinatario al correo electrónico utilizando la propiedad [To]() del objeto eml, si es necesario agrega la lista de CC (Copia Carbón) utilizando la propiedad [CC]() , la lista de BCC (Copia Carbón Oculta) utilizando la propiedad [Bcc]() y llama al método [Add]() con un nuevo objeto [MailAddress]() que contenga la dirección de correo electrónico y un nombre de visualización del destinatario.

**Ejemplo de código:**

```cs
// Carga eml desde un archivo
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// Una dirección de To con un nombre amigable también se puede especificar así
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Especifica la dirección de Cc y Bcc junto con un nombre amigable
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Equipo de Guangzhou"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Mostrar los asistentes opcionales en la salida del encabezado mht**

El siguiente ejemplo de código demuestra cómo usar la función *mostrar asistentes opcionales* al guardar un msg en formato mhtml:

```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

// Si necesitas omitir OptionalAttendees en el archivo mhtml, puedes limpiar la plantilla de formato para OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```

## **Establecer el cuerpo del correo**

En este artículo aprenderás a:

- [establecer el cuerpo de texto plano](#Setting-Plain-Text-Body)
- [establecer el cuerpo HTML](#Setting-HTML-Body)
- [establecer texto alternativo](#Setting-Alternate-Text)
- [especificar la codificación del cuerpo del correo](#Specifying-Mail-Body-Encoding)

### **Establecer el cuerpo de texto plano**

Se puede especificar un cuerpo de correo usando la propiedad [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

```cs
// Declara el mensaje como instancia de MailMessage
var eml = new MailMessage
{
    // Especifica HtmlBody
    Body = "Este es un cuerpo de texto plano"
};
```

### **Establecer el cuerpo HTML**

El cuerpo de un correo también se puede especificar usando la propiedad [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) de la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. 

```cs
// Declara el mensaje como instancia de MailMessage
var eml = new MailMessage
{
    // Especifica HtmlBody
    HtmlBody = "<html><body>Este es el cuerpo HTML</body></html>"
};
```

### **Establecer texto alternativo**

Una vista alternativa en un archivo EML es una representación adicional del contenido del correo electrónico que se puede usar para proporcionar una representación diferente del mensaje de correo. Por ejemplo, si envías un mensaje en HTML, también podrías querer proporcionar una versión **de texto plano** en caso de que algunos de los destinatarios usen lectores de correo electrónico que no pueden mostrar contenido HTML. Para ese propósito, usa la clase [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/). Esta clase tiene dos propiedades, [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) y [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), que se utilizan para resolver URLs dentro del contenido del correo.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) es una colección de objetos [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/). Cuando se representa, las URLs dentro del contenido del correo se comparan primero con las URLs en el enlace de contenido de cada objeto [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) en la colección [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) y se resuelven.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) es utilizado por el lector de correo para resolver URLs relativas dentro del cuerpo, y también para resolver URLs relativas de enlaces de contenido, en la colección [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/).

Considera el siguiente código con pasos detallados para establecer un texto alternativo.

**Pasos de código:**

1. Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Crea [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) para ver un mensaje de correo electrónico utilizando el contenido especificado en la cadena.
3. Agrega texto alternativo usando el método [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) de la colección [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/).

**Ejemplo de código:**
```cs
// Declara el mensaje como instancia de MailMessage
var eml = new MailMessage();

// Crea AlternateView para ver un mensaje de correo utilizando el contenido especificado en la cadena
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Texto Alternativo");

// Agregando texto alternativo
 eml.AlternateViews.Add(alternate);
```

### **Especificar la codificación del cuerpo del correo**

Aspose.Email utiliza la propiedad [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) de la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase para especificar la codificación del cuerpo del correo. Por ejemplo:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Configurar propiedades adicionales de MailMessage**

Con Aspose.Email, puedes utilizar propiedades adicionales de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) como:

- La propiedad [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) - establece **la fecha y hora** de un correo electrónico. Por defecto, la fecha es la fecha real en que se envió el mensaje, y la hora es el momento en que se envió, tal como lo muestra Microsoft Outlook. Sin embargo, el verdadero tiempo de entrega del correo se añade por el servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, donde [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) establece el campo Date.

   ```cs
   // Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-.NET
   
   // Agregado por el servidor SMTP en correos entregados
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
   
   // Agregado por el servidor SMTP en correos entregados
   Return-Path: <xyz@oikoscucine.it>
   
   // Agregado por el servidor SMTP en correos entregados
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: Para ABC
   
   // La fecha establecerá el campo Date, outlook mostrará esto como
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

- La enumeración [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) - especifica niveles de prioridad para el envío de un mensaje de correo electrónico. Puede ser baja, normal o alta. La prioridad influye en la velocidad de transmisión y entrega.
- La enumeración [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) - especifica cinco niveles de sensibilidad.
- [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/) - especifica el software que creó el mensaje de correo.

El siguiente fragmento de código ilustra cómo se pueden utilizar cada una de las propiedades discutidas anteriormente.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Algun asunto", "Algún texto de cuerpo")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Solicitar un recibo de lectura**

Para solicitar un [recibo de lectura](https://en.wikipedia.org/wiki/Return_receipt), usa la propiedad [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) de Aspose.Email de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Esta propiedad contiene los valores de la enumeración [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration).

Considera el siguiente **ejemplo de código**:

```cs
// Crea una instancia de la clase MailMessage
var eml = new MailMessage
{
    // Especifica campos From, To, HtmlBody, DeliveryNotificationOptions
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>Este es el cuerpo Html</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Crea una instancia de la clase SmtpClient
var client = new SmtpClient
{
    // Especifica tu servidor de correo, Nombre de usuario, Contraseña y Número de puerto
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};

try
{
    // Client.Send enviará este mensaje
    client.Send(eml);
    // Muestra ‘Mensaje Enviado’, solo si el mensaje fue enviado exitosamente
    Console.WriteLine(@"Mensaje enviado");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Nota**: Las solicitudes de recibos de lectura pueden no ser siempre cumplidas porque:

- Un cliente de correo puede no implementar esa funcionalidad.
- El usuario final puede tener esa funcionalidad deshabilitada.
- El usuario final puede optar por no enviar uno.

## **Establecer encabezados del correo**

Los encabezados de correo representan un estándar de Internet y la RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Un encabezado de correo se puede especificar usando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Los tipos comunes de encabezados están definidos en la clase [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). Es una clase sellada que funciona como una enumeración normal.

Normalmente, un encabezado de correo contiene estos campos:

- **To**: Las direcciones de los destinatarios se pueden especificar en el campo To. Los destinatarios del campo To son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- **From**: Este campo presenta la dirección de correo electrónico del remitente del mensaje.
- **Cc**: Permite a los usuarios enviar un mensaje como "Copia de carbón" o "Copia de cortesía". Es decir, no se espera que el receptor responda o actúe. Típicamente, se notifica al personal supervisor con CC.
- **Bcc**: Significa Copia de carbón oculta, que te permite enviar un correo a un destinatario que está oculto de otros destinatarios.
- **ReplyTo**: Este campo de encabezado está destinado a indicar a dónde quiere el remitente que vayan las respuestas.
- **Subject**: Título, encabezado, asunto. Utilizado a menudo como un indicador de hilo para los mensajes que responden o comentan sobre otros mensajes.
- **Date**: Este encabezado especifica una fecha (y hora). Normalmente, esta es la fecha en que el mensaje fue redactado y enviado.
- **XMailer**: Información sobre el software del cliente del originador. Ejemplo: X-Mailer: Aspose.Email. XMailer es utilizado por los clientes de correo. Diferentes clientes de correo tendrán diferentes valores de XMailer. El valor de XMailer de MS Outlook es Microsoft Office Outlook, Build 11.0.5510. Es ignorado por el receptor de correo o lector de correo.

Normalmente, un encabezado de correo se ve algo así:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: correo de prueba
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Para personalizar un encabezado de correo, sigue estos **pasos de código**:

- Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Especifica To, From, Cc, Bcc, ReplyTo, Subject, Date y XMailer usando una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Crea una instancia de la clase [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) y especifica el encabezado personalizado.
- Agrega el encabezado personalizado a la instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

El siguiente **fragmento de código** muestra cómo establecer encabezados de correo.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "correo de prueba",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

El fragmento de código anterior produce un encabezado de correo en el siguiente formato:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: correo de prueba
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Insertar un encabezado en una ubicación específica**

El método [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) de la clase [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) inserta un encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el método [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) no será útil. Para lograr esto, usa el método [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) de la [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes de otros encabezados con el mismo nombre. El siguiente fragmento de código muestra cómo insertar un encabezado en una ubicación específica.

```cs
eml.Headers.Insert("Received", "Valor");
```

### **Guardar todos los encabezados en MHTML**

La propiedad [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) de la clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) define si es necesario guardar todos los encabezados en la salida mhtml o no. El siguiente fragmento de código muestra cómo guardar todos los encabezados de un archivo mhtml:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Agregar encabezados personalizados al correo**

Un encabezado de correo se puede especificar usando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Para especificar un **encabezado personalizado** en un mensaje de correo, considera el siguiente ejemplo de código:

```cs
eml.Headers.Add("secret-header", "mystery");
```

El fragmento de código anterior produce un encabezado de correo en el siguiente formato:

```cs
secret-header: mystery
```

## **Guardar un archivo HTML con campos de tarea en un encabezado**

La enumeración [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) te permite especificar que los campos de tarea deben incluirse en el encabezado del archivo HTML guardado. El siguiente fragmento de código muestra cómo preservar los campos de tarea en un encabezado al guardar un archivo HTML:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Firmar correos electrónicos con DKIM**

> **_NOTA:_** La función solo está disponible para las versiones de la biblioteca que están dirigidas a .NET Framework. Las versiones que están dirigidas a .NET Core no tienen esta función.

Aspose.Email permite firmar correos electrónicos con DKIM (DomainKeys Identified Mail). Esto permite a una organización asumir la responsabilidad de un mensaje que está en tránsito ([Más información](https://www.dkim.org/)). DKIM añade una firma digital a los encabezados del mensaje de correo electrónico que puede ser validada por los receptores. La clave pública del remitente permite al receptor verificar que la firma coincide con el contenido del mensaje. El método [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) de la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase se utiliza para establecer la información criptográfica y de firma para firmar el mensaje. El siguiente fragmento de código muestra cómo firmar correos electrónicos con DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Algun asunto", "Algún texto de cuerpo");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```