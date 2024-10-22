---
title: "Trabajando con el Seguimiento y la Fecha de Vencimiento para Archivos MSG de Outlook"
url: /es/net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 60
type: docs
---


## **Configurando el Seguimiento y la Fecha de Vencimiento para Archivos MSG de Outlook**

Una bandera de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar mensajes y, en la configuración de la bandera, asignar una fecha de vencimiento para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para incitarlo a realizar el seguimiento del correo electrónico. Marcar correos electrónicos y establecer fechas de vencimiento programáticamente permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar tomar acción. Por ejemplo, podría utilizarse para enviar mensajes mensuales a un equipo de ventas para recordarles completar sus informes; o para enviar un mensaje a todo el personal para recordarles una reunión de la empresa. Aspose.Email para .NET admite la configuración de la bandera de seguimiento y la fecha de vencimiento para los objetos [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) utilizando [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) y [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). Hay varias variantes en las que se puede establecer la bandera de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código a continuación:

1. Establecer una bandera de seguimiento para un mensaje
1. Agregar una fecha de vencimiento y una fecha de recordatorio a un mensaje
1. Agregar una bandera al mensaje de un destinatario.
1. Marcar como completo.
1. Eliminar la bandera.
1. Leer opciones de seguimiento.

### **Configurando una bandera de Seguimiento**

El siguiente fragmento de código te muestra cómo establecer una bandera de seguimiento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Configurando Seguimiento para Destinatarios**

El siguiente fragmento de código te muestra cómo establecer seguimiento para destinatarios.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Marcando una bandera de Seguimiento como Completa**

El siguiente fragmento de código te muestra cómo marcar la bandera de seguimiento como completa.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Eliminando una bandera de Seguimiento**

El siguiente fragmento de código te muestra cómo eliminar la bandera de seguimiento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Leer opciones de bandera de seguimiento para un mensaje**

El siguiente fragmento de código te muestra cómo leer opciones de bandera de seguimiento para un mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}