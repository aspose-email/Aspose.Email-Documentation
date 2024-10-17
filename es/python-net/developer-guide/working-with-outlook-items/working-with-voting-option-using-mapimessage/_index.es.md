---
title: "Trabajando con la Opción de Votación Usando MapiMessage"
url: /es/python-net/trabajando-con-la-opcion-de-votacion-usando-mapimessage/
weight: 120
type: docs
---


## **Creando Opción de Votación Usando MapiMessage**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. La clase [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) proporciona la propiedad VotingButtons que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta.

### **Creando una Encuesta usando MapiMessage**

El siguiente ejemplo de código muestra cómo usar la propiedad *voting_buttons* de la clase [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) para crear una encuesta:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Establecer los botones de FollowUpOptions
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Sí;No;Quizás;¡Exactamente!"

msg.save("voting_btns.msg")
```

### **Leyendo Opciones de Votación de un MapiMessage**
El siguiente fragmento de código te muestra cómo leer las opciones de votación de un MapiMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}


### **Leyendo Solo Botones de Votación**
El siguiente fragmento de código te muestra cómo leer solo los botones de votación.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Agregando un botón de votación a un Mensaje Existente**
El siguiente fragmento de código te muestra cómo agregar un botón de votación a un mensaje existente.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Eliminando el botón de votación de un Mensaje**
El siguiente fragmento de código te muestra cómo eliminar el botón de votación de un Mensaje.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Leer la Información de Resultados de Voto**
El siguiente fragmento de código te muestra cómo leer la información de los resultados de voto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Establecer la bandera de mensaje no enviado**
El siguiente fragmento de código te muestra cómo muestrear los métodos utilizados en los ejemplos.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Mensaje marcado", "Hazlo agradable y breve, pero descriptivo. La descripción puede aparecer en las páginas de resultados de búsqueda de los motores de búsqueda...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```