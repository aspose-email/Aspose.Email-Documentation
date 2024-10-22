---
title: "Trabajando con la bandera de seguimiento y la fecha de vencimiento para archivos MSG de Outlook en C++"
description: "La bandera de seguimiento para los destinatarios y la fecha de vencimiento para los archivos MSG de Outlook se pueden establecer o eliminar utilizando la API de la Biblioteca de Análisis de Correo Electrónico en C++."
url: /es/cpp/working-with-follow-up-and-due-date-for-outlook-msg-files/
weight: 50
type: docs
linktitle: "Trabajando con la bandera de seguimiento y la fecha de vencimiento para archivos MSG de Outlook"
---

## **Configurando la bandera de seguimiento y la fecha de vencimiento para archivos MSG de Outlook**
Una bandera de seguimiento marca un mensaje de correo electrónico para algún tipo de acción. Microsoft Outlook permite a los usuarios marcar mensajes y, en la configuración de la bandera, asignar una fecha de vencimiento para el seguimiento. Microsoft Outlook envía un recordatorio al destinatario para recordarle que debe dar seguimiento al correo electrónico. Marcar correos electrónicos y establecer fechas de vencimiento programáticamente permite a los desarrolladores de software automatizar ciertos tipos de correos electrónicos y ayudar a los destinatarios a recordar que deben tomar acción. Por ejemplo, podría usarse para enviar mensajes mensuales a un equipo de ventas para recordarles que completen sus informes; o enviar un mensaje a todo el personal para recordarles una reunión de la empresa. Aspose.Email para C++ admite la configuración de la bandera de seguimiento y la fecha de vencimiento para los objetos MapiMessage utilizando FollowUpManager y FollowUpOptions. Hay una serie de variantes en las que se puede establecer la bandera de seguimiento en un mensaje. Todas se utilizan en el ejemplo de código a continuación:

1. Establecer una bandera de seguimiento para un mensaje.
1. Agregar una fecha de vencimiento y una fecha de recordatorio a un mensaje.
1. Agregar una bandera al mensaje de un destinatario.
1. Marcar como completado.
1. Eliminar la bandera.
1. Leer opciones de seguimiento.

### **Configurando una bandera de seguimiento**
El siguiente fragmento de código muestra cómo establecer una bandera de seguimiento utilizando la API de la Biblioteca de Análisis de Correo Electrónico en C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpflag-SetFollowUpflag.cpp" >}}

### **Configurando el seguimiento para los destinatarios**
El siguiente fragmento de código muestra cómo establecer el seguimiento para los destinatarios.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cpp" >}}

### **Marcando una bandera de seguimiento como completada**
El siguiente fragmento de código muestra cómo marcar la bandera de seguimiento como completada.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cpp" >}}

### **Eliminando una bandera de seguimiento**
El siguiente fragmento de código muestra cómo eliminar la bandera de seguimiento.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cpp" >}}

### **Leer las opciones de la bandera de seguimiento para un mensaje**
El siguiente fragmento de código muestra cómo leer las opciones de la bandera de seguimiento para un mensaje.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cpp" >}}