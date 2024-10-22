---
title: "Trabajando con el Seguimiento y la Fecha de Vencimiento para Archivos MSG de Outlook"
url: /es/java/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


## **Configurando el Seguimiento y la Fecha de Vencimiento para Archivos MSG de Outlook**

Una bandera de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar mensajes y, en la configuración de la bandera, asignar una fecha de vencimiento para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para que les impulse a hacer seguimiento al correo electrónico. Marcar correos electrónicos y establecer fechas de vencimiento programáticamente permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar que deben tomar acción. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarles completar sus informes; o para enviar un mensaje a todo el personal para recordarles una reunión de la empresa. Aspose.Email para Java admite la configuración de la bandera de seguimiento y la fecha de vencimiento para los objetos [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) utilizando [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) y [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/). Hay una serie de variantes en las que se puede establecer la bandera de seguimiento en un mensaje. Todas se utilizan en el siguiente ejemplo de código:

1. Establecer una bandera de seguimiento para un mensaje
1. Agregar una fecha de vencimiento y fecha de recordatorio a un mensaje
1. Agregar una bandera al mensaje de un destinatario.
1. Marcar como completo.
1. Eliminar la bandera.
1. Leer opciones de seguimiento.
   
### **Configurando una bandera de Seguimiento**

El siguiente fragmento de código muestra cómo establecer una bandera de seguimiento.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Este mensaje probará si se pueden agregar opciones de seguimiento a un nuevo mensaje mapi.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Seguimiento", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~

### **Configurando el Seguimiento para Destinatarios**

El siguiente fragmento de código muestra cómo establecer el seguimiento para destinatarios.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Este mensaje probará si se pueden agregar opciones de seguimiento a un nuevo mensaje mapi.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // marcar este mensaje como borrador

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Agregar la bandera de seguimiento para el destinatario ahora
FollowUpManager.setFlagForRecipients(mapi, "Seguimiento", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~

### **Marcando una bandera de Seguimiento como Completada**

El siguiente fragmento de código muestra cómo marcar la bandera de seguimiento como completada.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~

### **Eliminando una bandera de Seguimiento**

El siguiente fragmento de código muestra cómo eliminar la bandera de seguimiento.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~

### **Leer opciones de la bandera de seguimiento para un mensaje**

El siguiente fragmento de código muestra cómo leer las opciones de la bandera de seguimiento para un mensaje.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~