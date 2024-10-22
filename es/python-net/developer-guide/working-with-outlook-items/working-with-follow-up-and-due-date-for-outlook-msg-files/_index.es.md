---
title: "Trabajar con la bandera de seguimiento y la fecha de vencimiento para archivos MSG de Outlook"
url: /es/python-net/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---

Una bandera de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar mensajes y, en la configuración de la bandera, asignar una fecha de vencimiento para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para ayudarlo a seguir el correo electrónico. Marcar correos electrónicos y establecer fechas de vencimiento de forma programática permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar que deben tomar una acción. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarles que completen sus informes; o para enviar un mensaje a todo el personal para recordarles una reunión de la empresa. Aspose.Email para .NET soporta la configuración de la bandera de seguimiento y la fecha de vencimiento para los objetos MapiMessage utilizando FollowUpManager y FollowUpOptions. Hay varias variantes en las que se puede establecer la bandera de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código a continuación:

1. Establecer una bandera de seguimiento para un mensaje
1. Agregar una fecha de vencimiento y una fecha de recordatorio a un mensaje
1. Agregar una bandera al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Leer opciones de seguimiento.

## **Estableciendo una bandera de seguimiento**

El siguiente fragmento de código muestra cómo establecer una bandera de seguimiento.

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Crear un nuevo MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Este mensaje probará si se pueden agregar opciones de seguimiento a un nuevo mensaje MAPI."

# Convertir MailMessage a MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Definir opciones de seguimiento
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Seguimiento", dt_start_date, dt_due_date, dt_reminder_date)

# Establecer opciones de seguimiento para el MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Guardar el MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Estableciendo seguimiento para destinatarios**
El siguiente fragmento de código muestra cómo establecer seguimiento para destinatarios.

```py
import aspose.email as ae
from datetime import datetime

# Crear un nuevo MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Este mensaje probará si se pueden agregar opciones de seguimiento a un nuevo mensaje MAPI."

# Convertir MailMessage a MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Marcar el mensaje como borrador
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Agregar la bandera de seguimiento para destinatarios
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Seguimiento", dt_reminder_date)

# Guardar el MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Marcando una bandera de seguimiento como completada**

El siguiente fragmento de código muestra cómo marcar la bandera de seguimiento como completada.

```py
import aspose.email as ae

# Cargar el MapiMessage desde el archivo
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Marcar el mensaje como completado
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Guardar el MapiMessage actualizado
mapi_message.save("MarkedCompleted_out.msg")
```

## **Eliminando una bandera de seguimiento**
El siguiente fragmento de código muestra cómo eliminar la bandera de seguimiento.

```py
import aspose.email as ae

# Cargar el MapiMessage desde el archivo
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Limpiar la bandera de seguimiento
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Guardar el MapiMessage actualizado
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Leer opciones de bandera de seguimiento para un mensaje**

El siguiente fragmento de código muestra cómo leer las opciones de bandera de seguimiento para un mensaje.

```py
import aspose.email as ae

# Cargar el MapiMessage desde el archivo
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Obtener las opciones de seguimiento
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```