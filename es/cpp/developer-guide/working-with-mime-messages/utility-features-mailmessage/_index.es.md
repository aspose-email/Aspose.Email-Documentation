---
title: "Características de la utilidad - MailMessage"
description: "Puede leer los mensajes de correo electrónico con archivos adjuntos de TNEF utilizados por Microsoft Outlook y Exchange Server, y modificar el contenido del archivo adjunto mediante la API de biblioteca de analizadores de correo electrónico de C++."
url: /es/cpp/utility-features-mailmessage/
weight: 40
type: docs
---

## **Mensajes de correo que contienen archivos adjuntos de TNEF**
El formato de encapsulación neutral para el transporte (TNEF) es un formato patentado de archivos adjuntos de correo electrónico que utilizan Microsoft Outlook y Microsoft Exchange Server. La API Aspose.Email le permite leer los mensajes de correo electrónico que tienen archivos adjuntos en TNEF y modificar el contenido de los archivos adjuntos. Luego, el correo electrónico se puede guardar como correo electrónico normal o en el mismo formato, conservando los archivos adjuntos de TNEF. En este artículo se muestran diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos de TNEF. En este artículo también se muestra cómo trabajar con la creación de archivos EML de TNEF a partir de archivos MSG de Outlook.

### **Lectura del mensaje conservando los archivos adjuntos del TNEF**
El siguiente fragmento de código muestra cómo leer un mensaje conservando los archivos adjuntos de TNEF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}

## **Comprueba los mensajes devueltos**
Es muy común que un mensaje enviado a un destinatario rebote por cualquier motivo, como una dirección de destinatario no válida. La API Aspose.Email tiene la capacidad de procesar un mensaje de este tipo para comprobar si se trata de un correo electrónico devuelto o de un mensaje de correo electrónico normal. El método checkBounced de MailMessage devuelve un resultado válido si el mensaje de correo electrónico es un correo devuelto. Este artículo muestra el uso de la clase BounceResult, que proporciona la capacidad de comprobar si un mensaje es un correo electrónico devuelto. Además, proporciona información detallada sobre los destinatarios, las medidas adoptadas y el motivo de la notificación. El siguiente fragmento de código muestra cómo procesar los mensajes devueltos.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}
