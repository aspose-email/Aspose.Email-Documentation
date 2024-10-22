---
title: "Recursos de Utilidade - MailMessage"
url: /pt/python-net/utility-features-mailmessage/
weight: 40
type: docs
---

## **MailMessages Contendo Anexos TNEF**
O Formato de Encapsulamento Neutro de Transporte (TNEF) é um formato de anexo de e-mail proprietário usado pelo Microsoft Outlook e pelo Microsoft Exchange Server. A API Aspose.Email permite que você leia mensagens de e-mail que possuem anexos TNEF e modifique o conteúdo do anexo. O e-mail pode então ser salvo como um e-mail normal ou no mesmo formato, preservando os anexos TNEF. Este artigo mostra diferentes amostras de código para trabalhar com mensagens que contêm anexos TNEF. Este artigo também mostra como criar arquivos EML TNEF a partir de arquivos MSG do Outlook.
### **Lendo Mensagens Preservando Anexos TNEF**
O seguinte trecho de código mostra como ler mensagens preservando anexos TNEF.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# Isso preservará o anexo TNEF como está, o arquivo contém o anexo TNEF
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Criando EML TNEF a partir de MSG**
Os MSGs do Outlook às vezes contêm informações como tabelas e estilos de texto que podem ser disturbidos se forem convertidos para EML. Criar mensagens TNEF a partir de tais arquivos MSG permite reter a formatação e até enviar tais mensagens via clientes de e-mail preservando a formatação. A propriedade convert_as_tnef é usada para alcançar isso. O seguinte trecho de código mostra como criar EML TNEF a partir de MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

Para criar o TNEF, o seguinte código de exemplo pode ser usado.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# A opção PreserveTnefAttachments com MessageFormat.Msg criará o eml TNEF.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Detectar se uma Mensagem é TNEF**
O seguinte trecho de código mostra como detectar se uma mensagem é TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Processamento de Mensagens Devolvidas**
É muito comum que uma mensagem enviada a um destinatário possa ser devolvida por qualquer motivo, como endereço de destinatário inválido. A API Aspose.Email tem a capacidade de processar tal mensagem para verificar se é um e-mail devolvido ou uma mensagem de e-mail regular. O método check_bounced do MailMesage retorna um resultado válido se a mensagem de e-mail for um e-mail devolvido. Este artigo mostra o uso da classe [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) que fornece a capacidade de verificar se uma mensagem é um e-mail devolvido. Ele ainda fornece informações detalhadas sobre os destinatários, ação tomada e o motivo da notificação. O seguinte trecho de código mostra como processar mensagens devolvidas.

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
## **Analisador de Spam Bayesiano**
A Aspose.Email fornece filtragem de e-mails usando um analisador de spam bayesiano. Ele fornece a classe [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer) para esse propósito. Este artigo mostra como treinar o filtro para distinguir entre spam e e-mails regulares com base em um banco de dados de palavras.

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
        print("A mensagem é classificada como spam.")
    else:
        print("A mensagem é classificada como não spam.")
    print("Probabilidade de Spam: " + str(probability))
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