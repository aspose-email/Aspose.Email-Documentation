---
title: "Trabajando con el seguimiento y la fecha de vencimiento de los archivos MSG de Outlook"
url: /es/python-net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


Una marca de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar los mensajes y, en la configuración de la marca, asignar una fecha límite para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para pedirle que haga un seguimiento del correo electrónico. Marcar los correos electrónicos y establecer fechas de entrega mediante programación permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar las medidas que deben tomar. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarle que debe completar sus informes, o para enviar un mensaje a todo el personal para recordarles que se ha celebrado una reunión de la empresa. Aspose.Email para .NET permite configurar el indicador de seguimiento y la fecha de vencimiento para los objetos MapiMessage mediante FollowupManager y FollowupOptions. Hay varias variantes en las que se puede establecer el indicador de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código que aparece a continuación:

1. Establecer una marca de seguimiento para un mensaje
1. Añadir una fecha límite y una fecha de recordatorio a un mensaje
1. Añade una marca al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Lea las opciones de seguimiento.

## **Establecer una marca de seguimiento**

El siguiente fragmento de código muestra cómo establecer una marca FollowUp.

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Define follow-up options
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Follow Up", dt_start_date, dt_due_date, dt_reminder_date)

# Set follow-up options for the MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Save the MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Configuración del seguimiento de los destinatarios**
El siguiente fragmento de código muestra cómo configurar el seguimiento de los destinatarios.

```py
import aspose.email as ae
from datetime import datetime

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Mark the message as draft
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Add the follow-up flag for recipients
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Follow up", dt_reminder_date)

# Save the MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Marcar una marca de seguimiento como completada**

El siguiente fragmento de código muestra cómo marcar el indicador FollowUp como completado.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Mark the message as completed
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Save the updated MapiMessage
mapi_message.save("MarkedCompleted_out.msg")
```
## **Eliminar una marca de seguimiento**
El siguiente fragmento de código muestra cómo eliminar el indicador FollowUp.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Clear the follow-up flag
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Save the updated MapiMessage
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Leer las opciones de marca de seguimiento de un mensaje**

El siguiente fragmento de código muestra cómo leer las opciones de marca de seguimiento de un mensaje.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Get the follow-up options
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```
