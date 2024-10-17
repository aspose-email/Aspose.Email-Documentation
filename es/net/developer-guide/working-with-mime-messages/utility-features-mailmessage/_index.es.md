---
title: "Funciones de Utilidad - MailMessage"
url: /es/net/utility-features-mailmessage/
weight: 50
type: docs
---


## **Cifrado y Descifrado de Mensajes**

Aspose.Email proporciona la facilitat de cifrar y descifrar mensajes de correo electrónico utilizando X509Certificates. Este artículo muestra cómo se puede cargar y cifrar un mensaje existente o nuevo utilizando [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Los métodos [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) y [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) devuelven un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para los efectos aplicados y deben cuidarse al cifrar/descifrar mensajes. Cifrar y descifrar mensajes implica los siguientes pasos:

1. Crear un nuevo mensaje o cargar uno existente
1. Cargar un certificado de cifrado utilizando el objeto X509Certificate
1. Cifrar el mensaje utilizando el certificado
1. Enviar el mensaje o guardarlo
1. Descifrar el mensaje según sea necesario

El siguiente fragmento de código muestra cómo cifrar y descifrar mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Verificar si un Mensaje está Cifrado**

La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) de Aspose.Email te permite verificar si un mensaje está cifrado o no. La propiedad [IsEncrypted](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/) de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) permite verificar esto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Mensajes de correo electrónico que contienen adjuntos TNEF**

El Formato de Encapsulación Neutral de Transporte (TNEF) es un formato propietario de adjunto de correo electrónico utilizado por Microsoft Outlook y Microsoft Exchange Server. La API de Aspose.Email te permite leer mensajes de correo electrónico que tienen adjuntos TNEF y modificar el contenido del adjunto. El correo electrónico se puede guardar como un correo electrónico normal o en el mismo formato, preservando los adjuntos TNEF. Este artículo muestra diferentes ejemplos de código para trabajar con mensajes que contienen adjuntos TNEF. Este artículo también muestra cómo crear archivos TNEF EML a partir de archivos MSG de Outlook.

### **Leer un Mensaje Preservando Adjuntos TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje preservando adjuntos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Leer un Mensaje sin Preservar Adjuntos TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje sin preservar adjuntos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Actualizar Recursos en un Adjunto TNEF y Preservar el Formato TNEF**

El siguiente fragmento de código muestra cómo actualizar recursos en un adjunto TNEF y preservar el formato TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Agregar Nuevos Adjuntos al Mensaje Principal que Contiene TNEF**

El siguiente fragmento de código muestra cómo agregar nuevos adjuntos al mensaje principal que contiene TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Crear TNEF EML a partir de MSG**

Los MSGs de Outlook a veces contienen información como tablas y estilos de texto que pueden verse alteradas si se convierten a EML. Crear mensajes TNEF a partir de dichos archivos MSG permite conservar el formato e incluso enviar tales mensajes a través de clientes de correo electrónico conservando el formato. La propiedad [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) se utiliza para lograr esto. El siguiente fragmento de código muestra cómo crear TNEF EML a partir de MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

Para crear el TNEF, se puede utilizar el siguiente código de muestra.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Detectar si un Mensaje es TNEF**

El siguiente fragmento de código muestra cómo detectar si un mensaje es TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Verificar si el Adjunto está en formato TNEF**

La propiedad [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) permite detectar si el adjunto del mensaje es un mensaje en formato TNEF.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"¿Es el adjunto TNEF?: {attachment.IsTnef}");
}
```

## **Procesar Mensajes Rebotados**

Es muy común que un mensaje enviado a un destinatario pueda rebotar por cualquier razón, como una dirección de destinatario inválida. La API de Aspose.Email tiene la capacidad de procesar tal mensaje para verificar si es un correo electrónico rebotado o un mensaje de correo electrónico regular. El método [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) devuelve un resultado válido si el mensaje de correo electrónico es un correo rebotado. Este artículo muestra el uso de la clase [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/) que proporciona la capacidad de verificar si un mensaje es un correo electrónico rebotado. Además, proporciona información detallada sobre los destinatarios, la acción tomada y la razón de la notificación. El siguiente fragmento de código muestra cómo procesar mensajes rebotados.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}


## **Analizador de Spam Bayesiano**

Aspose.Email proporciona filtrado de correo electrónico utilizando un analizador de spam bayesiano. Proporciona la clase [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) para este propósito. Este artículo muestra cómo entrenar el filtro para distinguir entre spam y correos electrónicos regulares basándose en la base de datos de palabras.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Obtener preámbulo y epílogo de mensajes eml**

Un mensaje de correo electrónico puede contener alguna información oculta como texto simple antes del cuerpo del mensaje (es decir, preámbulo) o después del cuerpo (es decir, epílogo). Normalmente, es información adicional o contexto para el destinatario antes o después de que lean el contenido principal del correo electrónico. Puedes obtener esta información usando las propiedades [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) o/and [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) respectivamente.

El siguiente fragmento de código muestra cómo obtener los textos del preámbulo y del epílogo:

```cs
// Obtiene o establece un texto de preámbulo.
public string Preamble

// Obtiene o establece un texto de epílogo.
public string Epilogue
```