---
title: Утилиты - MailMessage
type: docs
weight: 40
url: /python-net/utility-features-mailmessage/
---


## **MailMessages с вложениями TNEF**
Transport Neutral Encapsulation Format (TNEF) — это собственный формат вложений электронной почты, используемый Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать электронные сообщения, имеющие вложения TNEF, и изменять содержимое вложения. Затем электронное письмо может быть сохранено как обычное письмо или в том же формате, сохраняя вложения TNEF. В этой статье представлены различные примеры кода для работы с сообщениями, содержащими вложения TNEF. Также в статье показано, как создавать EML-файлы TNEF из файлов MSG Outlook.
### **Чтение сообщений с сохранением вложений TNEF**
Следующий фрагмент кода показывает, как читать сообщения, сохраняя вложения TNEF.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# Это сохранит вложение TNEF как есть, файл содержит вложение TNEF
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Создание TNEF EML из MSG**
MSG-файлы Outlook иногда содержат информацию, такую как таблицы и текстовые стили, которые могут быть нарушены при конвертации в EML. Создание TNEF-сообщений из таких файлов MSG позволяет сохранить форматирование и даже отправлять такие сообщения через почтовые клиенты с сохранением форматирования. Для этого используется свойство convert_as_tnef. Следующий фрагмент кода показывает, как создать TNEF EML из MSG.

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
# Опция PreserveTnefAttachments с MessageFormat.Msg создаст TNEF eml.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Определение, является ли сообщение TNEF**
Следующий фрагмент кода показывает, как определить, является ли сообщение TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Обработка возвратов сообщений**
Очень часто сообщение, отправленное получателю, может быть возвращено по любой причине, например, из-за недействительного адреса получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение, чтобы проверить, является ли оно возвращенной электронной почтой или обычным электронным сообщением. Метод check_bounced класса MailMessage возвращает действительный результат, если электронное сообщение является возвращенной электронной почтой. В этой статье показано использование класса [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/), который предоставляет возможность проверки, является ли сообщение возвращенным. Он также предоставляет подробную информацию о получателях, принятых мерах и причинах уведомления. Следующий фрагмент кода показывает, как обрабатывать возвращаемые сообщения.

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
Aspose.Email предоставляет фильтрацию электронной почты с помощью байесовского анализатора спама. Для этой цели предоставляется класс [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer). В этой статье показано, как обучить фильтр различать спам и обычные электронные письма на основе базы данных слов.

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
        print("Сообщение классифицируется как спам.")
    else:
        print("Сообщение классифицируется как не спам.")
    print("Вероятность спама: " + str(probability))
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