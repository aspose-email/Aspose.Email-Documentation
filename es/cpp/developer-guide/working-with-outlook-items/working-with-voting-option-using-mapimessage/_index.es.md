---
title: "Trabajando con la opción de votación usando MapiMessage"
url: /es/cpp/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---

## **Creación de una opción de votación con MapiMessage**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. La clase FollowupOptions proporciona la propiedad VotingButtons que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un mapiMessage con opciones de votación para crear una encuesta.
### **Lectura de las opciones de votación desde un mapiMessage**
El siguiente fragmento de código muestra cómo leer las opciones de votación desde un MAPIMessage.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVotingOptions-ReadingVotingOptions.cpp" >}}
### **Botones de votación de solo lectura**
El siguiente fragmento de código muestra cómo leer solo los botones de votación.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cpp" >}}
### **Agregar el botón de votación a un mensaje existente**
El siguiente fragmento de código muestra cómo añadir un botón de votación a un mensaje existente.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cpp" >}}
### **Eliminar el botón de votación de un mensaje**
El siguiente fragmento de código muestra cómo eliminar el botón de votación de un mensaje.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cpp" >}}
### **Lea la información sobre los resultados de la votación**
El siguiente fragmento de código muestra cómo leer la información de los resultados de las votaciones.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cpp" >}}
