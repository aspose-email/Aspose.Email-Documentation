---
title: "Características de Utilidad - MailMessage"
url: /es/python-net/utility-features-mailmessage/
weight: 40
type: docs
---


## **MailMessages que Contienen Archivos Adjuntos TNEF**
El Formato de Encapsulación Neutral de Transporte (TNEF) es un formato de archivo adjunto de correo electrónico propietario utilizado por Microsoft Outlook y Microsoft Exchange Server. La API Aspose.Email te permite leer mensajes de correo electrónico que tienen archivos adjuntos TNEF y modificar el contenido del archivo adjunto. El correo electrónico puede luego ser guardado como un correo electrónico normal o en el mismo formato, preservando los archivos adjuntos TNEF. Este artículo muestra diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos TNEF. Este artículo también muestra cómo crear archivos EML TNEF desde archivos MSG de Outlook.
### **Leyendo Mensajes Preservando Archivos Adjuntos TNEF**
El siguiente fragmento de código muestra cómo leer un mensaje preservando los archivos adjuntos TNEF.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# Esto preservará el archivo adjunto TNEF tal como está, el archivo contiene el archivo adjunto TNEF
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Creando EML TNEF desde MSG**
Los MSG de Outlook a veces contienen información como tablas y estilos de texto que pueden verse alterados si se convierten a EML. Crear mensajes TNEF a partir de tales archivos MSG permite retener el formato e incluso enviar tales mensajes a través de los clientes de correo electrónico manteniendo el formato. La propiedad convert_as_tnef se utiliza para lograr esto. El siguiente fragmento de código muestra cómo crear EML TNEF desde MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

Para crear el TNEF, se puede utilizar el siguiente código de muestra.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# La opción PreserveTnefAttachments con MessageFormat.Msg creará el eml TNEF.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Detectar si un Mensaje es TNEF**
El siguiente fragmento de código muestra cómo detectar si un mensaje es TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Procesamiento de Mensajes Rebotados**
Es muy común que un mensaje enviado a un destinatario pueda rebotar por cualquier razón, como una dirección de destinatario no válida. La API Aspose.Email tiene la capacidad de procesar dicho mensaje para verificar si es un correo electrónico rebotado o un mensaje de correo electrónico regular. El método check_bounced de MailMessage devuelve un resultado válido si el mensaje de correo electrónico es un correo electrónico rebotado. Este artículo muestra el uso de la clase [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) que proporciona la capacidad de verificar si un mensaje es un correo electrónico rebotado. Además, proporciona información detallada sobre los destinatarios, la acción tomada y la razón de la notificación. El siguiente fragmento de código muestra cómo procesar mensajes rebotados.

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
## **Analizador de Spam Bayesiano**
Aspose.Email proporciona filtrado de correo electrónico utilizando un analizador de spam bayesiano. Ofrece la clase [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer) para este propósito. Este artículo muestra cómo entrenar el filtro para distinguir entre spam y correos electrónicos regulares basado en una base de datos de palabras.

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
        print("El mensaje se clasifica como spam.")
    else:
        print("El mensaje se clasifica como no spam.")
    print("Probabilidad de Spam: " + str(probability))
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