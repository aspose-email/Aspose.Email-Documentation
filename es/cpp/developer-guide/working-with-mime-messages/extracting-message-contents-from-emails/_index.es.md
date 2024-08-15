---
title: "Extraer el contenido de los mensajes de los correos electrónicos en C++"
description: "Con la biblioteca de analizadores de correo electrónico de C++, puede acceder a las propiedades de los mensajes de correo electrónico, a la información del encabezado y manipularlos de diferentes maneras mediante programación."
url: /es/cpp/extracting-message-contents-from-emails/
weight: 20
type: docs
linktitle: "Extraer el contenido de los mensajes de los correos electrónicos"
---

## **Mostrar información de correo electrónico en la pantalla**
The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades de los mensajes de correo electrónico. La información del encabezado (que se explica en Extracción de encabezados de correo electrónico) se puede extraer y manipular de diferentes maneras. En este artículo se explica cómo mostrar la información del encabezado del correo electrónico seleccionado y el cuerpo del correo electrónico en la pantalla. Para mostrar la información del correo electrónico en la pantalla, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
- Cargue un mensaje de correo electrónico en [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) instance.
- Muestra el contenido del correo electrónico en la pantalla.

El siguiente fragmento de código de C++ muestra cómo mostrar la información del correo electrónico en la pantalla.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Extracción de encabezados de correo electrónico**
El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y RFC que se incluye en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) clase. Los tipos de encabezados comunes se definen en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal. Para extraer los encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. Cargue un mensaje de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. Una vez que se haya cargado un mensaje de correo electrónico, obtendremos su contenido sin procesar.

The [`MailMessage`](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) la clase en sí contiene propiedades como From, To, Cc, Subject, etc. Estas propiedades se pueden extraer de los encabezados.

1. Muestra el contenido sin procesar.

El siguiente fragmento de código de C++ muestra cómo extraer los encabezados de los correos electrónicos.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Obtener valores de encabezado decodificados**
El siguiente fragmento de código muestra cómo obtener valores de encabezado decodificados.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}
