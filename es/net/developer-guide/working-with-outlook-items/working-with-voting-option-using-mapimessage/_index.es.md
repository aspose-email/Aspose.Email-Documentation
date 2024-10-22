---
title: "Trabajando con la Opción de Votación Usando MapiMessage"
url: /es/net/working-with-voting-option-using-mapimessage/
weight: 50
type: docs
---


## **Creando Opción de Votación Usando MapiMessage**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. La clase [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) proporciona la propiedad [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) con opciones de votación para crear una encuesta.

### **Creando una Encuesta usando MapiMessage**

El siguiente fragmento de código muestra cómo crear una encuesta, la clase [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) se puede usar como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Leyendo Opciones de Votación de un MapiMessage**

El siguiente fragmento de código muestra cómo leer opciones de votación de un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Leyendo Solo Botones de Votación**

El siguiente fragmento de código muestra cómo leer solo botones de votación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Agregando un botón de votación a un Mensaje Existente**

El siguiente fragmento de código muestra cómo agregar un botón de votación a un mensaje existente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Eliminando un botón de Votación de un Mensaje**

El siguiente fragmento de código muestra cómo eliminar el botón de votación de un Mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Leer la Información de Resultados de Votación**

El siguiente fragmento de código muestra cómo leer la información de resultados de votación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Métodos de Ejemplo Usados en Ejemplos**

El siguiente fragmento de código muestra cómo crear el mensaje de ejemplo utilizado en los ejemplos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}