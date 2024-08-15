---
title: "Trabajando con el seguimiento y la fecha de vencimiento de los archivos MSG de Outlook"
url: /es/java/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
---


## **Configuración de la fecha de seguimiento y vencimiento de los archivos MSG de Outlook**

Una marca de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar los mensajes y, en la configuración de la marca, asignar una fecha límite para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para pedirle que haga un seguimiento del correo electrónico. Marcar los correos electrónicos y establecer fechas de entrega mediante programación permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar las medidas que deben tomar. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarle que debe completar sus informes, o para enviar un mensaje a todo el personal para recordarles que se ha celebrado una reunión de la empresa. Aspose.Email para Java permite establecer un indicador de seguimiento y una fecha límite para [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) objetos que utilizan [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/). Hay varias variantes en las que se puede establecer el indicador de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código que aparece a continuación:

1. Establecer una marca de seguimiento para un mensaje
1. Añadir una fecha límite y una fecha de recordatorio a un mensaje
1. Añade una marca al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Lea las opciones de seguimiento.
  
### **Establecer una marca de seguimiento**

El siguiente fragmento de código muestra cómo establecer una marca de seguimiento.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Follow Up", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~

### **Configuración del seguimiento de los destinatarios**

En el siguiente fragmento de código, se muestra cómo configurar el seguimiento de los destinatarios.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // mark this message as draft

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Add the follow up flag for recipient now
FollowUpManager.setFlagForRecipients(mapi, "Follow up", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~

### **Marcar una marca de seguimiento como completada**

El siguiente fragmento de código muestra cómo marcar la marca de seguimiento como completada.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~

### **Eliminar una marca de seguimiento**

En el siguiente fragmento de código, se muestra cómo eliminar la marca de seguimiento.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~

### **Leer las opciones de marca de seguimiento de un mensaje**

El siguiente fragmento de código muestra cómo leer las opciones de marca de seguimiento de un mensaje.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~
