---
title: "Extracción de Contenidos de Mensajes de Correos Electrónicos en C++"
description: "Usando la Biblioteca de Análisis de Emails en C++, puedes acceder a las propiedades del mensaje de correo electrónico, información del encabezado y manipularlo de diferentes maneras programáticamente."
url: /es/cpp/extracting-message-contents-from-emails/
weight: 20
type: docs
linktitle: "Extracción de Contenidos de Mensajes de Correos Electrónicos"
---

## **Mostrando Información del Correo Electrónico en Pantalla**
La [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información del encabezado (discutida en Extracción de Encabezados de Correos Electrónicos) puede ser extraída y manipulada de diferentes maneras. Este artículo explica cómo mostrar información seleccionada del encabezado de correo electrónico y el cuerpo del correo en pantalla. Para mostrar la información del correo electrónico en la pantalla, sigue estos pasos:

- Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Carga un mensaje de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Muestra el contenido del correo electrónico en la pantalla.

El siguiente fragmento de código C++ te muestra cómo mostrar información del correo electrónico en la pantalla.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Extracción de Encabezados de Correos Electrónicos**
El encabezado del correo electrónico representa un conjunto de campos de encabezado estándar definidos por Internet y RFC incluidos en los mensajes de correo electrónico. Un encabezado de correo electrónico puede ser especificado usando la clase [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message). Los tipos de encabezados comunes están definidos en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal. Para extraer encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. Carga un mensaje de correo electrónico en la instancia de la clase [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. Después de que se haya cargado un mensaje de correo electrónico, obtendremos su contenido en bruto.

La clase [`MailMessage`](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) contiene propiedades como De, Para, Cc, Asunto, etc. Estas propiedades pueden ser extraídas de los encabezados.

1. Muestra el contenido en bruto.

El siguiente fragmento de código C++ te muestra cómo extraer encabezados de correos electrónicos.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Obtener Valores de Encabezado Decodificados**
El siguiente fragmento de código te muestra cómo obtener valores de encabezado decodificados.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}