---
title: "Функции утилиты — MailMessage"
url: /ru/python-net/utility-features-mailmessage/
weight: 40
type: docs
---


## **Почтовые сообщения, содержащие вложения в формате TNEF**
Транспортный нейтральный формат инкапсуляции (TNEF) — это собственный формат вложений электронной почты, используемый Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать сообщения электронной почты, содержащие вложения в формате TNEF, и изменять содержимое вложения. Затем письмо можно сохранить как обычное электронное письмо или в том же формате, сохранив вложения TNEF. В этой статье приведены различные примеры кода для работы с сообщениями, содержащими вложения в формате TNEF. В этой статье также описывается работа с созданием файлов TNEF EML из файлов Outlook MSG.
### **Чтение сообщения путем сохранения вложений TNEF**
В следующем фрагменте кода показано, как читать сообщения, сохраняя вложения в формате TNEF.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# This will Preserve the TNEF attachment as it is, file contains the TNEF attachment
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Создание EML TNEF из MSG**
Иногда файлы MSG Outlook содержат такую информацию, как таблицы и текстовые стили, которые могут нарушить работу при преобразовании в формат EML. Создание сообщений TNEF из таких файлов MSG позволяет сохранить форматирование и даже отправлять такие сообщения через почтовые клиенты с сохранением форматирования. Для этого используется свойство convert_as_tnef. В следующем фрагменте кода показано, как создать TNEF eML из MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

Для создания TNEF можно использовать следующий пример кода.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# The PreserveTnefAttachments option with MessageFormat.Msg will create the TNEF eml.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Определите, соответствует ли сообщение TNEF**
В следующем фрагменте кода показано, как определить, является ли сообщение TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Обработка возвращенных сообщений**
Очень часто сообщение, отправленное получателю, может возвращаться по любой причине, например, по неправильному адресу получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение для проверки того, является ли оно отведенным письмом или обычным сообщением электронной почты. Метод mailMessage check_bounced возвращает действительный результат, если сообщение электронной почты было отклонено. В этой статье показано использование [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) класс, который позволяет проверить, является ли сообщение возвращенным письмом. Кроме того, в нем содержится подробная информация о получателях, предпринятых действиях и причине уведомления. В следующем фрагменте кода показано, как обрабатывать возвращенные сообщения.

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
## **Байесовский анализатор спама**
Aspose.Email обеспечивает фильтрацию электронной почты с помощью байесовского спам-анализатора. Он предоставляет [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer) класс для этой цели. В этой статье показано, как научить фильтр отличать спам от обычных писем на основе базы слов.

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
