---
title: "Extracción de Contenidos de Mensajes de Correos Electrónicos"
url: /es/python-net/extracting-message-contents-from-emails/
weight: 20
type: docs
---


## **Mostrando Información del Correo Electrónico en Pantalla**
MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores acceder a las propiedades del mensaje. La información del encabezado (discutida en Extracción de Encabezados de Correos Electrónicos) puede ser extraída y manipulada de diferentes maneras. Este artículo explica cómo mostrar la información del encabezado del correo electrónico seleccionado y el cuerpo del correo en pantalla. Para Mostrar Información del Correo Electrónico en Pantalla, siga estos pasos:

- Cree una instancia de la clase MailMessage.
- Cargue un mensaje de correo electrónico en la instancia de MailMessage.
- Muestre el contenido del correo en pantalla.

El siguiente fragmento de código le muestra cómo mostrar información del correo electrónico en pantalla.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayEmailInformation-DisplayEmailInformation.py" >}}
## **Extracción de Encabezados de Correos Electrónicos**
El encabezado del correo electrónico representa un conjunto estándar de campos de encabezado definidos por Internet y RFC que se incluyen en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico utilizando la clase MailMessage. Los tipos de encabezados comunes están definidos en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal. Para extraer encabezados de un correo electrónico, siga estos pasos:

1. Cree una instancia de la clase MailMessage.
1. Cargue un mensaje de correo electrónico en la instancia de la clase MailMessage.
1. Después de que se haya cargado un mensaje de correo electrónico, obtendremos su contenido en bruto.

La clase MailMessage en sí contiene propiedades como De, Para, Cc, Asunto, etc. Estas propiedades se pueden extraer de los encabezados.

1. Muestre el contenido en bruto.

El siguiente fragmento de código le muestra cómo extraer encabezados de correos electrónicos.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractingEmailHeaders-ExtractingEmailHeaders.py" >}}
## **Obtener Valores de Encabezados Decodificados**
El siguiente fragmento de código le muestra cómo obtener valores de encabezados decodificados.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-GetDecodedHeaderValues-GetDecodedHeaderValues.py" >}}