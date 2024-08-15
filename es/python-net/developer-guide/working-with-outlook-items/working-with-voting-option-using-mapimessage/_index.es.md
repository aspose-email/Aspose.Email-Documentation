---
title: "Trabajando con la opción de votación usando MapiMessage"
url: /es/python-net/working-with-voting-option-using-mapimessage/
weight: 120
type: docs
---


## **Creación de una opción de votación con MapiMessage**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. El [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) La clase proporciona la propiedad VotingButtons que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un mapiMessage con opciones de votación para crear una encuesta.

### **Creación de una encuesta con MapiMessage**

En el siguiente ejemplo de código se muestra cómo utilizar el *voting_buttons* propiedad del [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) clase para crear una encuesta:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Set FollowUpOptions Buttons
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Yes;No;Maybe;Exactly!"

msg.save("voting_btns.msg")
```

### **Lectura de las opciones de votación desde un mapiMessage**
El siguiente fragmento de código muestra cómo leer las opciones de votación desde un MAPIMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}


### **Botones de votación de solo lectura**
El siguiente fragmento de código muestra cómo leer solo los botones de votación.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Agregar el botón de votación a un mensaje existente**
El siguiente fragmento de código muestra cómo añadir un botón de votación a un mensaje existente.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Eliminar el botón de votación de un mensaje**
El siguiente fragmento de código muestra cómo eliminar el botón de votación de un mensaje.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Lea la información sobre los resultados de la votación**
El siguiente fragmento de código muestra cómo leer la información de los resultados de las votaciones.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Establecer marca de mensajes no enviados**
El siguiente fragmento de código muestra cómo muestrear los métodos utilizados en los ejemplos.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Flagged message", "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```
