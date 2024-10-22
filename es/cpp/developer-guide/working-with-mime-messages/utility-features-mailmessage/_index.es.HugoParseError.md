---
title: Funciones de utilidad - MailMessage
type: docs
weight: 40
url: /cpp/utility-features-mailmessage/
description: Puede leer mensajes de correo electrónico con archivos adjuntos TNEF utilizados por Microsoft Outlook y Exchange Server, y modificar el contenido del archivo adjunto utilizando la API de la Biblioteca de Análisis de Correo Electrónico en C++.
---

## **MailMessages que contienen archivos adjuntos TNEF**

El Formato de Encapsulación Neutral de Transporte (TNEF) es un formato de archivo adjunto de correo electrónico propietario utilizado por Microsoft Outlook y Microsoft Exchange Server. La API de Aspose.Email le permite leer mensajes de correo electrónico que tienen archivos adjuntos TNEF y modificar el contenido del archivo adjunto. El correo electrónico puede ser guardado como un correo electrónico normal o en el mismo formato, preservando los archivos adjuntos TNEF. Este artículo muestra diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos TNEF. Este artículo también muestra cómo crear archivos EML TNEF a partir de archivos MSG de Outlook.

### **Lectura de mensajes preservando archivos adjuntos TNEF**

El siguiente fragmento de código le muestra cómo leer un mensaje preservando los archivos adjuntos TNEF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}

## **Comprobar mensajes devueltos**

Es muy común que un mensaje enviado a un destinatario pueda rebotar por cualquier motivo, como una dirección de destinatario no válida. La API de Aspose.Email tiene la capacidad de procesar dicho mensaje para verificar si es un correo electrónico rebotado o un mensaje de correo electrónico regular. El método CheckBounced de MailMessage devuelve un resultado válido si el mensaje de correo electrónico es un correo rebotado. Este artículo muestra el uso de la clase BounceResult que proporciona la capacidad de verificar si un mensaje es un correo electrónico rebotado. Además, proporciona información detallada sobre los destinatarios, la acción tomada y la razón de la notificación. El siguiente fragmento de código le muestra cómo procesar mensajes rebotados.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}

