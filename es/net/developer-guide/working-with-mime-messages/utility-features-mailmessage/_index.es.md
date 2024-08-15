---
title: "Características de la utilidad - MailMessage"
url: /es/net/utility-features-mailmessage/
weight: 50
type: docs
---


## **Cifrado y descifrado de mensajes**

Aspose.Email ofrece la posibilidad de cifrar y descifrar los mensajes de correo electrónico mediante los certificados X509. Este artículo muestra cómo se puede cargar y cifrar un mensaje nuevo o existente mediante [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) and [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) los métodos devuelven un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) son el objeto de los efectos aplicados y hay que tenerlo en cuenta al cifrar o descifrar los mensajes. El cifrado y descifrado de los mensajes implica los siguientes pasos:

1. Crea un mensaje nuevo o carga uno existente
1. Cargue un certificado de cifrado con el objeto X509Certificate
1. Cifrar el mensaje con el certificado
1. Enviar el mensaje o guardarlo
1. Descifra el mensaje según sea necesario

El siguiente fragmento de código muestra cómo cifrar y descifrar mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Comprobar el cifrado de un mensaje**

Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase le permite comprobar si un mensaje está cifrado o no. El [IsEncrypted ](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/)propiedad de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) le permite comprobar esto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Mensajes de correo electrónico que contienen archivos adjuntos de TNEF**

El formato de encapsulación neutral para el transporte (TNEF) es un formato patentado de archivos adjuntos de correo electrónico que utilizan Microsoft Outlook y Microsoft Exchange Server. La API Aspose.Email le permite leer los mensajes de correo electrónico que tienen archivos adjuntos en TNEF y modificar el contenido de los archivos adjuntos. Luego, el correo electrónico se puede guardar como un correo electrónico normal o en el mismo formato, conservando los archivos adjuntos de TNEF. En este artículo se muestran diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos de TNEF. Este artículo también muestra cómo crear archivos EML de TNEF a partir de archivos MSG de Outlook.

### **Lea un mensaje que conserva los archivos adjuntos de TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje que conserva los archivos adjuntos de TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Leer un mensaje sin conservar los archivos adjuntos de TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje sin conservar los archivos adjuntos de TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Actualización de recursos en un archivo adjunto TNEF y conservación del formato TNEF**

El siguiente fragmento de código muestra cómo actualizar los recursos de un archivo adjunto TNEF y conservar el formato TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Agregar nuevos archivos adjuntos al mensaje principal que contiene TNEF**

El siguiente fragmento de código muestra cómo agregar nuevos archivos adjuntos al mensaje principal que contiene TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Creación de TNEF EML a partir de MSG**

Los mensajes de Outlook a veces contienen información como tablas y estilos de texto que pueden alterarse si se convierten a EML. La creación de mensajes TNEF a partir de estos archivos MSG permite conservar el formato e incluso enviar dichos mensajes a través de los clientes de correo electrónico que conservan el formato. El [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) la propiedad se usa para lograr esto. El siguiente fragmento de código muestra cómo crear TNEF EML a partir de MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

Para crear el TNEF, se puede usar el siguiente código de ejemplo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Detectar si un mensaje es TNEF**

El siguiente fragmento de código muestra cómo detectar si un mensaje es TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Compruebe si el archivo adjunto está en formato TNEF**

The [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) La propiedad permite detectar si el archivo adjunto del mensaje es un mensaje con formato TNEF.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"Is Attachment TNEF?: {attachment.IsTnef}");
}
```

## **Procesamiento de mensajes devueltos**

Es muy común que un mensaje enviado a un destinatario rebote por cualquier motivo, como una dirección de destinatario no válida. La API Aspose.Email tiene la capacidad de procesar un mensaje de este tipo para comprobar si se trata de un correo electrónico devuelto o de un mensaje de correo electrónico normal. La [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase devuelve un resultado válido si el mensaje de correo electrónico es un correo devuelto. Este artículo muestra el uso del [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/) clase que proporciona la capacidad de comprobar si un mensaje es un correo electrónico devuelto. Además, proporciona información detallada sobre los destinatarios, las medidas adoptadas y el motivo de la notificación. El siguiente fragmento de código muestra cómo procesar los mensajes devueltos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}


## **Analizador bayesiano de spam**

Aspose.Email proporciona filtrado de correo electrónico mediante un analizador de spam bayesiano. Proporciona la [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) clase para este propósito. Este artículo muestra cómo entrenar el filtro para que distinga entre el correo basura y el correo normal basándose en la base de datos de palabras.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Obtención del preámbulo y el epílogo de los mensajes eml**

Un mensaje de correo electrónico puede contener información oculta como texto plano antes del cuerpo del mensaje (es decir, el preámbulo) o después del cuerpo (es decir, el epílogo). Por lo general, se trata de información o contexto adicionales para el destinatario antes o después de leer el contenido principal del correo electrónico. Puede obtener esta información utilizando [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) or/and [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) propiedades respectivamente.

El siguiente fragmento de código muestra cómo obtener los textos del preámbulo y del epílogo:

```cs
// Gets or sets a preamble text.
public string Preamble

// Gets or sets an epilogue text.
public string Epilogue
```
