---
title: "Trabajando con el seguimiento y la fecha de vencimiento de los archivos MSG de Outlook"
url: /es/net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 60
type: docs
---


## **Configuración de la fecha de seguimiento y vencimiento de los archivos MSG de Outlook**

Una marca de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar los mensajes y, en la configuración de la marca, asignar una fecha límite para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para pedirle que haga un seguimiento del correo electrónico. Marcar los correos electrónicos y establecer fechas de entrega mediante programación permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar las medidas que deben tomar. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarle que debe completar sus informes, o para enviar un mensaje a todo el personal para recordarles que se ha celebrado una reunión de la empresa. Aspose.Email para .NET permite establecer un indicador de seguimiento y una fecha límite para el [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objetos que utilizan [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). Hay varias variantes en las que se puede establecer el indicador de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código que aparece a continuación:

1. Establecer una marca de seguimiento para un mensaje
1. Añadir una fecha límite y una fecha de recordatorio a un mensaje
1. Añade una marca al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Lea las opciones de seguimiento.

### **Establecer una marca de seguimiento**

El siguiente fragmento de código muestra cómo establecer una marca de seguimiento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Configuración del seguimiento de los destinatarios**

En el siguiente fragmento de código, se muestra cómo configurar el seguimiento de los destinatarios.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Marcar una marca de seguimiento como completada**

El siguiente fragmento de código muestra cómo marcar la marca de seguimiento como completada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Eliminar una marca de seguimiento**

En el siguiente fragmento de código, se muestra cómo eliminar la marca de seguimiento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Leer las opciones de marca de seguimiento de un mensaje**

El siguiente fragmento de código muestra cómo leer las opciones de marca de seguimiento de un mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}
