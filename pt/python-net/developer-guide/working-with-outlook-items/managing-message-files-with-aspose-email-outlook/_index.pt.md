---
title: "Gerenciando Arquivos de Mensagem com Aspose.Email.Outlook"
url: /pt/python-net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Determinar o tipo de item MAPI em uma pasta PST**

Um arquivo PST geralmente contém vários tipos de dados, como mensagens de email, eventos de calendário, contatos e mais. A classe [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) do Aspose.Email permite acessar e categorizar diferentes tipos de itens MAPI dentro de um arquivo PST. O código abaixo demonstra como determinar o tipo de um item MAPI em uma pasta PST:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Obter o tipo da classe com base em msg.SupportedType
    item_type = msg.supported_type

    # Tipo não suportado. Não pode ser acessado como o tipo de item apropriado.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Tipo de item não suportado")
    # Uma mensagem de email.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # Você pode acessar as propriedades de MapiMessage lá.
        # Um assunto, por exemplo
        print(msg.subject)
    # Um item de contato. Pode ser acessado como MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiContact lá. 
        # Um name_info.display_name, por exemplo. 
        print(contact.name_info.display_name)
    # Um item de calendário. Pode ser acessado como MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiCalendar lá. 
        # Uma localização, por exemplo. 
        print(calendar.location)
    # Uma lista de distribuição. Pode ser acessada como MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiDistributionList lá
    # Uma entrada de diário. Pode ser acessada como MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiJournal lá
    # Um StickyNote. Pode ser acessado como MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiNote lá
    # Um item de tarefa. Pode ser acessado como MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # Você pode acessar as propriedades de MapiTask lá

```

## **Convertendo MSG para mensagem MIME**
A API Aspose.Email fornece a capacidade de converter arquivos MSG em mensagens MIME usando o método ToMailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Definindo o Timeout para Conversão e Carregamento de uma Mensagem**

Para limitar o tempo em milissegundos da conversão de mensagens (valor padrão 3 seg), a propriedade **timeout** da classe [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class) é utilizada.

Veja como você pode definir um timeout para os processos de conversão e carregamento de mensagens:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

Ao definir um timeout para os processos de conversão e carregamento de mensagens, você pode controlar o tempo máximo que essas operações estão autorizadas a durar. Após definir o timeout, você pode prosseguir com seus processos de conversão e carregamento de mensagens.

## **Processamento de Arquivos de Template do Outlook (OFT)**

### **Carregar, Modificar e Salvar um Arquivo OFT**

Os templates do Outlook (OFT) oferecem uma maneira conveniente de simplificar o processo de envio de mensagens de email repetitivas. Em vez de compor o mesmo email do zero a cada vez, você pode criar uma mensagem no Outlook e salvá-la como um Template do Outlook (OFT). Mais tarde, sempre que precisar enviar uma mensagem semelhante, pode gerá-la rapidamente a partir do template. Essa abordagem economiza o esforço de reescrever o mesmo conteúdo no corpo da mensagem, especificando a linha de assunto, formatação e mais.

A classe [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) do Aspose.Email fornece uma ferramenta poderosa para carregar e manipular arquivos de template do Outlook (OFT). Uma vez que um template do Outlook é carregado em uma instância da classe MailMessage, você pode facilmente atualizar propriedades como remetente, destinatário, corpo da mensagem, assunto e vários outros atributos.

```py
import aspose.email as ae

# Carregar o arquivo OFT
oft_file_path = "seu_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Atualizar propriedades conforme necessário
mail_message.subject = "Assunto Atualizado"
mail_message.body = "Texto do corpo atualizado."

# Salvar a mensagem atualizada como um arquivo MSG
msg_file_path = "mensagem_atualizada.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Mensagem atualizada salva em {msg_file_path}")
```
Após fazer as atualizações necessárias, você pode enviar o email usando a classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class):

```py
# Enviar o email
smtpClient.send(message)
```

### **Salvando um arquivo MSG do Outlook como Template**

Para isso, você pode usar a classe [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) para criar um email e, em seguida, salvá-lo como um arquivo OFT. O seguinte exemplo de código mostrará como salvar um email como um Template do Outlook:

```py
import aspose.email as ae

# Criar um novo MailMessage
message = ae.MailMessage()
message.subject = "Template de Outlook Exemplo"
message.html_body = "<html><body>Este é o corpo do email.</body></html>"
message.from_address = ae.MailAddress("seu.email@exemplo.com", "Seu Nome")

# Salvar o MailMessage como um arquivo Template do Outlook (OFT)
oft_file_path = "template_exemplo.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Template do Outlook salvo como {oft_file_path}")
```
### **OFT ou MSG: Determinar o tipo de um MapiMessage**

O seguinte exemplo de código ilustra como determinar se uma mensagem MAPI carregada representa uma mensagem de email padrão ou um Template do Outlook (OFT):

```py
msg = ae.mapi.MapiMessage.Load("mensagem.msg");
isOft = msg.is_template # retorna false

msg = ae.mapi.MapiMessage.Load("mensagem.oft");
isOft = msg.IsTemplate; # retorna true
```
Após carregar o arquivo MSG, o código verifica se a propriedade **is_template** da classe [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) é True ou False. Caso retorne *false*, a mensagem carregada é uma mensagem de email padrão, não um Template do Outlook; caso contrário, se retornar *true*, a mensagem não é uma mensagem de email padrão, é um Template do Outlook.

### **Salvando MapiMessage ou MailMessage como OFT**

A [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) é uma classe base abstrata para classes que permitem ao usuário especificar opções adicionais ao salvar um MailMessage em um formato específico. O seguinte exemplo de código demonstra como salvar uma mensagem no formato OFT:

```py
import aspose.email as ae

# Salvar o MailMessage no formato OFT
eml = ae.MailMessage.load("mensagem.eml")

eml.save("mensagem.oft", ae.SaveOptions.default_oft)

# ou alternativa maneira 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("mensagem.oft", save_options)

# ou alternativa maneira 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("mensagem.oft", save_options)

# Salvar o MapiMessage no formato OFT
msg = ae.mapi.MapiMessage.load("mensagem.msg")

msg.save("mensagem.oft", ae.SaveOptions.default_oft)

# ou alternativa maneira 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("mensagem.oft", save_options)

# ou alternativa maneira 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("mensagem.oft", save_options)
```

## **Gerenciando Mensagens com Assinaturas Digitais**

A biblioteca fornece a classe [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class), uma classe base abstrata para classes que permitem ao usuário especificar opções adicionais ao carregar um MailMessage de um formato específico. A opção de preservação de assinatura é definida por padrão.

### **Converter de EML para MSG Preservando Assinatura**

O exemplo de código abaixo demonstra como carregar uma mensagem, convertê-la para formato MSG e salvar como MSG (a assinatura é preservada por padrão):

```python

import aspose.email as ae

# Carregar a mensagem de email
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Mensagem.eml", loadOptions)
# Salvar como MSG
message.save("ConverterEMLParaMSG_saida.msg", ae.SaveOptions.default_msg_unicode)
```

### **Converter Mensagens S/MIME de MSG para EML**

Aspose.Email permite converter de MSG para EML preservando uma assinatura digital, como mostrado no seguinte exemplo de código.

```python
import aspose.email as ae

# Carregar a mensagem de email
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Salvar arquivo no disco
msg.save("ConverterMensagensMIMEDoMSGParaEML_saida.msg")
```
## **Definir Categoria de Cor para Arquivos MSG do Outlook**

Às vezes, você pode precisar diferenciar emails de importância particular e organizá-los visualmente. A biblioteca fornece uma maneira de fazer isso ao atribuir uma cor específica a um item de mensagem. Quando você define uma categoria de cor para um item, isso permite que você identifique e localize facilmente itens relacionados à primeira vista. Use a classe [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) para definir a categoria de cor para uma mensagem como no seguinte exemplo de código:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Adicionar duas categorias
ae.mapi.FollowUpManager.add_category(msg, "Categoria Roxa")
ae.mapi.FollowUpManager.add_category(msg, "Categoria Vermelha")

# Recuperar a lista de categorias disponíveis
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Remover a categoria especificada e então limpar todas as categorias
ae.mapi.FollowUpManager.remove_category(msg, "Categoria Vermelha")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Acessando Informações de Acompanhamento de um arquivo MSG**

### **Extrair Informações de Recibo de Leitura e Entrega**

O exemplo de código abaixo demonstra como extrair informações do destinatário e seu status de rastreamento de um arquivo de mensagem do Outlook (MSG):

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Destinatário: {recipient.display_name}")
    print(f"Hora de entrega:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Hora de leitura:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Criando Mensagens de Encaminhamento e Resposta**

Aspose.Email fornece maneiras diretas de criar mensagens de encaminhamento e resposta com base nas existentes.

### **Criando uma Mensagem de Encaminhamento**

Você pode usar a classe [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) para criar uma mensagem de encaminhamento definindo a mensagem de origem, remetente, destinatários, assunto e corpo. Mensagens de encaminhamento podem incluir a mensagem original como um anexo ou como o corpo da mensagem encaminhada. Você tem a flexibilidade de personalizar propriedades adicionais como anexos, cabeçalhos e opções de formatação. O exemplo de código abaixo mostra como criar uma mensagem de encaminhamento:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("encaminhar_saida.msg")

```

### **Criando uma Mensagem de Resposta**

A classe [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) é usada para configurar as opções de resposta, incluindo a mensagem de origem, remetente, destinatários, modo de resposta, prefixo de assunto e o corpo da mensagem de resposta. Mensagens de resposta podem ser criadas em diferentes modos de resposta como "Responder ao Remetente" ou "Responder a Todos", conforme sua necessidade. Você pode personalizar várias propriedades como anexos, cabeçalhos e opções de formatação para a mensagem de resposta. O exemplo de código abaixo mostra como criar uma mensagem de resposta:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Definir Propriedades do ReplyMessageBuilder
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Caro Amigo,</b></p> O que quero fazer é apresentar meu co-autor e co-professor. <p><a href=\"www.google.com\">Este é o primeiro link</a></p><p><a href=\"www.google.com\">Este é o segundo link</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("responder_saida.msg")

```