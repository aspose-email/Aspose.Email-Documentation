---
title: "Trabajando con la Opción de Votación Usando MapiMessage"
url: /es/cpp/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---

## **Creando Opción de Votación Usando MapiMessage**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. La clase FollowUpOptions proporciona la propiedad VotingButtons que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta.
### **Leyendo Opciones de Votación desde un MapiMessage**
El siguiente fragmento de código muestra cómo leer opciones de votación desde un MapiMessage.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVotingOptions-ReadingVotingOptions.cpp" >}}
### **Leyendo Solo Botones de Votación**
El siguiente fragmento de código muestra cómo leer solo botones de votación.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cpp" >}}
### **Agregando un botón de votación a un Mensaje Existente**
El siguiente fragmento de código muestra cómo agregar un botón de votación a un mensaje existente.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cpp" >}}
### **Eliminando un botón de votación de un Mensaje**
El siguiente fragmento de código muestra cómo eliminar un botón de votación de un mensaje.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cpp" >}}
### **Leer la Información de Resultados de Votación**
El siguiente fragmento de código muestra cómo leer la información de los resultados de la votación.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cpp" >}}