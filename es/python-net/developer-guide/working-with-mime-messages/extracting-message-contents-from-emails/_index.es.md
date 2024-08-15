---
title: "Extraer el contenido de los mensajes de los correos electrónicos"
url: /es/python-net/extracting-message-contents-from-emails/
weight: 20
type: docs
---


## **Mostrar información de correo electrónico en la pantalla**
El MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje de correo electrónico. La información del encabezado (que se explica en Extracción de encabezados de correo electrónico) se puede extraer y manipular de diferentes maneras. En este artículo se explica cómo mostrar la información del encabezado del correo electrónico seleccionado y el cuerpo del correo electrónico en la pantalla. Para mostrar la información del correo electrónico en la pantalla, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Carga un mensaje de correo electrónico en la instancia de MailMessage.
- Muestra el contenido del correo electrónico en la pantalla.

El siguiente fragmento de código muestra cómo mostrar la información del correo electrónico en la pantalla.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayEmailInformation-DisplayEmailInformation.py" >}}
## **Extracción de encabezados de correo electrónico**
El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definido por Internet y RFC que se incluye en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante la clase MailMessage. Los tipos de encabezados comunes se definen en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal. Para extraer los encabezados de un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Carga un mensaje de correo electrónico en la instancia de la clase MailMessage.
1. Una vez que se haya cargado un mensaje de correo electrónico, obtendremos su contenido sin procesar.

La clase MailMessage en sí contiene propiedades como From, To, Cc, Subject, etc. Estas propiedades se pueden extraer de los encabezados.

1. Muestra el contenido sin procesar.

El siguiente fragmento de código muestra cómo extraer los encabezados de los correos electrónicos.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractingEmailHeaders-ExtractingEmailHeaders.py" >}}
## **Obtener valores de encabezado decodificados**
El siguiente fragmento de código muestra cómo obtener valores de encabezado decodificados.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-GetDecodedHeaderValues-GetDecodedHeaderValues.py" >}}
