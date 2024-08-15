---
title: "Trabajando con el seguimiento y la fecha de vencimiento de los archivos MSG de Outlook en C++"
description: "El indicador de seguimiento de los destinatarios y la fecha de vencimiento de los archivos MSG de Outlook se pueden configurar o eliminar mediante la API de biblioteca analizadora de correo electrónico de C++."
url: /es/cpp/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
linktitle: "Trabajando con el seguimiento y la fecha de vencimiento de los archivos MSG de Outlook"
---

## **Configuración de la fecha de seguimiento y vencimiento de los archivos MSG de Outlook**
Una marca de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar los mensajes y, en la configuración de la marca, asignar una fecha límite para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para pedirle que haga un seguimiento del correo electrónico. Marcar los correos electrónicos y establecer fechas de entrega mediante programación permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar las medidas que deben tomar. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarle que debe completar sus informes, o para enviar un mensaje a todo el personal para recordarles que se ha celebrado una reunión de la empresa. Aspose.Email para C++ permite configurar el indicador de seguimiento y la fecha de vencimiento para los objetos MapiMessage mediante FollowupManager y FollowupOptions. Hay varias variantes en las que se puede establecer el indicador de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código que aparece a continuación:

1. Establecer una marca de seguimiento para un mensaje
1. Añadir una fecha límite y una fecha de recordatorio a un mensaje
1. Añade una marca al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Lea las opciones de seguimiento.

### **Establecer una marca de seguimiento**
El siguiente fragmento de código muestra cómo establecer un indicador de seguimiento mediante la API de biblioteca de analizadores de correo electrónico de C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpflag-SetFollowUpflag.cpp" >}}

### **Configuración del seguimiento de los destinatarios**
El siguiente fragmento de código muestra cómo configurar el seguimiento de los destinatarios.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cpp" >}}

### **Marcar una marca de seguimiento como completada**
El siguiente fragmento de código muestra cómo marcar el indicador FollowUp como completado.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cpp" >}}

### **Eliminar una marca de seguimiento**
El siguiente fragmento de código muestra cómo eliminar el indicador FollowUp.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cpp" >}}

### **Leer las opciones de marca de seguimiento de un mensaje**
El siguiente fragmento de código muestra cómo leer las opciones de marca de seguimiento de un mensaje.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cpp" >}}
