---
title: "Carregando, Visualizando e Analisando Arquivo MSG"
url: /pt/python-net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


Este tópico explica como carregar um arquivo de mensagem do Microsoft Outlook (*.msg). A classe [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) é usada para carregar arquivos MSG e fornece várias funções de carregamento estáticas para diferentes cenários. O seguinte trecho de código mostra como carregar arquivos MSG de um arquivo ou de um stream.
{{% alert %}}
**Experimente!**

Analise arquivos de email online com o gratuito [**Aspose.Email Parser App**](https://products.aspose.app/email/pt/parser).
{{% /alert %}}
## **Carregando Arquivos MSG**
O seguinte trecho de código mostra como carregar arquivos MSG.

```py
from aspose.email.mapi import MapiMessage

# Cria uma instância de MapiMessage a partir de um arquivo
msg = MapiMessage.from_file("message.msg")

# Obtém o assunto
print("Assunto: " + msg.subject)

# Obtém o endereço de origem
print("De: " + msg.sender_email_address)

# Obtém o corpo
print("Corpo: " + msg.body)

# Obtém informações dos destinatários
recipients = ", ".join([r.email_address for r in msg.recipients])
print("Destinatários: " + recipients)

# Obtém os anexos
for att in msg.attachments:
    print(att.file_name)
    print(att.display_name)
```
## **Carregando a partir de Stream**
O seguinte trecho de código mostra como carregar um arquivo a partir de um stream.

```py
from aspose.email.mapi import MapiMessage
import io

# Lê o arquivo em um array de bytes
file_path = dir_path + "message.msg"
with open(file_path, "rb") as file:
    bytes_data = file.read()

# Cria um stream de memória a partir do array de bytes
stream = io.BytesIO(bytes_data)
stream.seek(0)

# Cria uma instância de MapiMessage a partir do stream
msg = MapiMessage.from_stream(stream)

# Obtém o assunto
print("Assunto: " + msg.subject)

# Obtém o endereço de origem
print("De: " + msg.sender_email_address)

# Obtém o corpo
print("Corpo: " + msg.body)
```

## **Convertendo EML para MSG preservando o formato EML incorporado**
Arquivos EML podem ser carregados na classe [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) instanciando um objeto [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) e passando-o para o método MapiMessage.from_mail_message. Se o arquivo EML contiver arquivos EML incorporados, use MapiConversionOptions.PreserveEmbeddedMessageFormat para preservar o formato dos arquivos EML incorporados. O código abaixo mostra como carregar arquivos EML no MapiMessage enquanto preserva o formato dos arquivos EML incorporados.

```py
from aspose.email import MailMessage, EmlLoadOptions
from aspose.email.mapi import MapiMessage, MapiConversionOptions, OutlookMessageFormat

eml_file = dir_path + "message.eml"

# Carrega o arquivo EML
eml_options = EmlLoadOptions()
eml = MailMessage.load(eml_file, eml_options)

# Cria MapiConversionOptions
conversion_options = MapiConversionOptions()
conversion_options.format = OutlookMessageFormat.UNICODE

# Preserva o Formato da Mensagem Incorporada
conversion_options.preserve_embedded_message_format = True

# Converte EML para MSG com opções
msg = MapiMessage.from_mail_message(eml, conversion_options)
```