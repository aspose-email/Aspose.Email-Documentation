---
title: "Características de la utilidad - MailMessage"
url: /es/python-net/utility-features-mailmessage/
weight: 40
type: docs
---


## **Mensajes de correo que contienen archivos adjuntos de TNEF**
El formato de encapsulación neutral para el transporte (TNEF) es un formato patentado de archivos adjuntos de correo electrónico que utilizan Microsoft Outlook y Microsoft Exchange Server. La API Aspose.Email le permite leer los mensajes de correo electrónico que tienen archivos adjuntos en TNEF y modificar el contenido de los archivos adjuntos. Luego, el correo electrónico se puede guardar como correo electrónico normal o en el mismo formato, conservando los archivos adjuntos de TNEF. En este artículo se muestran diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos de TNEF. En este artículo también se muestra cómo trabajar con la creación de archivos EML de TNEF a partir de archivos MSG de Outlook.
### **Lectura del mensaje conservando los archivos adjuntos del TNEF**
El siguiente fragmento de código muestra cómo leer un mensaje conservando los archivos adjuntos de TNEF.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# This will Preserve the TNEF attachment as it is, file contains the TNEF attachment
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Creación de TNEF EML a partir de MSG**
Los mensajes de Outlook a veces contienen información, como tablas y estilos de texto, que puede resultar molesta si se convierten a EML. La creación de mensajes TNEF a partir de estos archivos MSG permite conservar el formato e incluso enviar dichos mensajes a través de los clientes de correo electrónico que conservan el formato. Para ello se utiliza la propiedad convert_as_tnef. El siguiente fragmento de código muestra cómo crear TNEF eML a partir de MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

Para crear el TNEF, se puede usar el siguiente código de ejemplo.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# The PreserveTnefAttachments option with MessageFormat.Msg will create the TNEF eml.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Detectar si un mensaje es TNEF**
El siguiente fragmento de código muestra cómo detectar si un mensaje es TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Procesamiento de mensajes devueltos**
Es muy común que un mensaje enviado a un destinatario rebote por cualquier motivo, como una dirección de destinatario no válida. La API Aspose.Email tiene la capacidad de procesar un mensaje de este tipo para comprobar si se trata de un correo electrónico devuelto o de un mensaje de correo electrónico normal. El método check_bounced de MailMessage devuelve un resultado válido si el mensaje de correo electrónico es un correo devuelto. Este artículo muestra el uso de [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) clase que proporciona la capacidad de comprobar si un mensaje es un correo electrónico devuelto. Además, proporciona información detallada sobre los destinatarios, las medidas adoptadas y el motivo de la notificación. El siguiente fragmento de código muestra cómo procesar los mensajes devueltos.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

mail = MailMessage.load(data_dir + "message.eml")
result = mail.check_bounced()

print("IsBounced: " + str(result.is_bounced))
print("Action: " + str(result.action))
print("Recipient: " + str(result.recipient))
print()
print("Reason: " + str(result.reason))
print("Status: " + str(result.status))
print()
```
## **Analizador bayesiano de spam**
Aspose.Email proporciona filtrado de correo electrónico mediante un analizador de spam bayesiano. Proporciona la [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer) clase para este propósito. Este artículo muestra cómo entrenar el filtro para que distinga entre el correo basura y el correo normal basándose en una base de datos de palabras.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode
from aspose.email.antispam import SpamAnalyzer
import os

ham_folder = "/hamFolder"
spam_folder = "/Spam"
test_folder = data_dir
database_file = "SpamFilterDatabase.txt"

def print_result(probability):
    if probability >= 0.5:
        print("The message is classified as spam.")
    else:
        print("The message is classified as not spam.")
    print("Spam Probability: " + str(probability))
    print()

def teach_and_create_database(ham_folder, spam_folder, database_file):
    analyzer = SpamAnalyzer(database_file)
    analyzer.teach_from_directory(ham_folder, True)
    analyzer.teach_from_directory(spam_folder, False)
    analyzer.save_database()

teach_and_create_database(ham_folder, spam_folder, database_file)

test_files = [f for f in os.listdir(test_folder) if f.endswith(".eml")]
analyzer = SpamAnalyzer(database_file)

for file in test_files:
    file_path = os.path.join(test_folder, file)
    msg = MailMessage.load(file_path)
    print(msg.subject)
    probability = analyzer.test(msg)
    print_result(probability)
```
