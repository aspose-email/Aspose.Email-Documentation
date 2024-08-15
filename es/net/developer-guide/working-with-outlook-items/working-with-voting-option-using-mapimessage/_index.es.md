---
title: "Trabajando con la opción de votación usando MapiMessage"
url: /es/net/working-with-voting-option-using-mapimessage/
weight: 50
type: docs
---


## **Creación de una opción de votación con MapiMessage**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. El [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) la clase proporciona la [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) propiedad que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) con opciones de votación para crear una encuesta.

### **Creación de una encuesta con MapiMessage**

El siguiente fragmento de código muestra cómo crear una encuesta, el [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) la clase se puede usar como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Lectura de las opciones de votación desde un mapiMessage**

El siguiente fragmento de código muestra cómo leer las opciones de votación de un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Botones de votación de solo lectura**

El siguiente fragmento de código muestra cómo leer solo los botones de votación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Añadir un botón de votación a un mensaje existente**

El siguiente fragmento de código muestra cómo añadir un botón de votación a un mensaje existente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Eliminar un botón de votación de un mensaje**

El siguiente fragmento de código muestra cómo eliminar el botón de votación de un mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Lea la información sobre los resultados de la votación**

El siguiente fragmento de código muestra cómo leer la información de los resultados de las votaciones.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Métodos de muestra utilizados en los ejemplos**

El siguiente fragmento de código muestra cómo crear el mensaje de ejemplo utilizado en los ejemplos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}
