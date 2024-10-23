---
title: "Trabalhando com Anexos de Mensagem"
url: /pt/python-net/working-with-message-attachments/
weight: 70
type: docs
---

## **Gerenciando Anexos com Aspose Outlook**
Criar e Salvar Arquivos de Mensagem do Outlook (MSG) explicou como criar e salvar mensagens, e como criar arquivos MSG com anexos. Este artigo explica como gerenciar anexos do Microsoft Outlook com Aspose.Email. Anexos de um arquivo de mensagem são acessados e salvos em disco usando a propriedade Attachments da classe MapiMessage. A propriedade Attachments é uma coleção do tipo MapiAttachmentCollection.

### **Verificar se o Anexo é Inline ou Regular**

"Inline" e "Regular" referem-se à forma como são incluídos em uma mensagem de email. **Anexos Regulares** são arquivos anexados da maneira tradicional. Eles geralmente são exibidos em uma lista dentro do cliente de email e podem ser baixados por um destinatário e salvos em um armazenamento local. Anexos **Inline**, também conhecidos como imagens incorporadas ou inline, são tipicamente usados para incluir imagens ou outros meios dentro do corpo do email. Eles não são exibidos em uma lista separada, mas são mostrados diretamente dentro do conteúdo do email, como no corpo do email. Isso permite incluir imagens ou outros meios que fazem parte do conteúdo da mensagem. O exemplo de código abaixo demonstra como determinar se um anexo é inline ou regular:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Salvar Anexos de um arquivo de Mensagem do Outlook (MSG)**

Para salvar anexos de um arquivo MSG:

1. Itere através da coleção MapiAttachmentCollection e obtenha os anexos individuais.
1. Para salvar os anexos, chame o método Save() da classe MapiAttachment.

O seguinte trecho de código mostra como salvar anexos no disco local.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Crie uma instância de MapiMessage a partir do arquivo
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Itere pela coleção de anexos
for attachment in message.attachments:
    # Salve o anexo individual
    attachment.save(data_dir + attachment.file_name)
```

### **Obter Anexos de Mensagem de Email Aninhados**

Anexos OLE incorporados também aparecem na coleção Attachments da classe MapiMessage. O seguinte exemplo de código analisa um arquivo de mensagem em busca de anexos de mensagem incorporados e os salva em disco. O método estático FromProperties() da classe MapiMessage pode criar uma nova mensagem a partir de um anexo incorporado. O seguinte trecho de código mostra como obter anexos de mensagem de email aninhados.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Crie um objeto MapiMessage a partir do anexo individual
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Crie um objeto do tipo MailMessageInterpreter a partir da mensagem acima e salve a mensagem incorporada em um arquivo no disco
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Removendo Anexos**

A biblioteca Aspose Outlook fornece a funcionalidade para remover anexos de arquivos de Mensagem do Microsoft Outlook (.msg):

- Chame o método RemoveAttachments(). Ele aceita o caminho do arquivo de mensagem como parâmetro. Ele é implementado como um método estático público, portanto, você não precisa instanciar o objeto.

O seguinte trecho de código mostra como remover anexos.

```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

Você também pode chamar o método estático DestoryAttachment() da classe MapiMessage. Ele funciona mais rápido que RemoveAttachment(), porque o método RemoveAttachment() analisa o arquivo de mensagem.

```py
import aspose.email as ae

# Destrói anexos na MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Adicionando Anexos MSG**

Uma mensagem do Outlook pode conter outras mensagens do Microsoft Outlook em anexos, seja como mensagens regulares ou incorporadas. A MapiAttachmentCollection fornece membros sobrecarregados do método Add para criar mensagens do Outlook com ambos os tipos de anexos.
{{% alert %}}
**Experimente!**

Adicione ou remova anexos de email online com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}

### **Adicionar um Anexo de Referência a um MapiMessage**

"Anexo de referência" refere-se geralmente a um anexo que contém uma referência ou link para um recurso externo em vez do arquivo real. Essas referências são frequentemente usadas em emails HTML para vincular a imagens ou recursos externos hospedados em um servidor remoto. Em vez de incorporar o arquivo inteiro, um anexo de referência inclui uma URL ou referência ao conteúdo externo.

Aspose.Email fornece um conjunto de ferramentas para exibir anexos de referência corretamente apresentado no seguinte exemplo de código:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Adicione um anexo de referência
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# Você também pode definir propriedades adicionais do anexo
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Finalmente salve a mensagem
msg.save("msg_with_ref_attach.msg")
```

### **Incorporar uma Mensagem como Anexo**
O seguinte trecho de código mostra como anexar arquivos MSG incorporados em um arquivo MSG que contém um PR_ATTACH_METHOD cujo valor é igual a 5.

```py
import aspose.email as ae

# Crie uma nova MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "Este é o corpo de uma mensagem")

# Carregue a mensagem de anexo
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Adicione o anexo à mensagem
message.attachments.add("Relatório Semanal.msg", attach_msg)

# Salve a mensagem com o anexo de mensagem incorporada
message.save("WithEmbeddedMsg_out.msg")
```
### **Ler Mensagens Incorporadas de Anexos**
O seguinte trecho de código mostra como ler uma mensagem incorporada de um anexo.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Carregue a MapiMessage a partir do arquivo
message = ae.mapi.MapiMessage.from_file(file_name)

# Verifique se o primeiro anexo é uma mensagem do Outlook
if message.attachments[0].object_data.is_outlook_message:
    # Obtenha a mensagem incorporada como MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Execute mais operações com a mensagem incorporada
    # ...
```
## **Inserção e Substituição de Anexos**
A API Aspose.Email fornece a capacidade de inserir anexos em um índice específico na mensagem principal. Também fornece a funcionalidade de substituir o conteúdo de um anexo por outro anexo de mensagem. O seguinte trecho de código mostra como funciona a inserção e substituição de anexos.
### **Inserir em Localização Específica**
A API Aspose.Email fornece a capacidade de inserir um anexo MSG a um MSG pai usando o método Insert da MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). O seguinte trecho de código mostra como inserir em uma localização específica.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Carregue a MapiMessage a partir do arquivo
message = ae.mapi.MapiMessage.load(file_name)

# Salve o anexo em um fluxo de memória
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Carregue o anexo do fluxo de memória
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Insira o anexo carregado no índice 1
message.attachments.insert(1, "new 11", get_data)
```
### **Substituir Conteúdos do Anexo**
Isso pode ser usado para substituir os conteúdos de um anexo incorporado por novos usando o método Replace. No entanto, não pode ser usado para inserir um anexo com PR_ATTACH_NUM = 4 (por exemplo) na coleção com collection.Count = 2. O seguinte trecho de código mostra como substituir os conteúdos do anexo.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Carregue a MapiMessage a partir do arquivo
message = ae.mapi.MapiMessage.load(file_name)

# Salve o anexo em um fluxo de memória
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Carregue o anexo do fluxo de memória
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Substitua o anexo no índice 1 pelo anexo carregado
message.attachments.replace(1, "new 1", get_data)
```
### **Renomear um Anexo em um MapiMessage**

É possível modificar os nomes de exibição dos anexos em mensagens de email carregadas de um arquivo. O exemplo de código abaixo mostra como fazer isso:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "Novo nome de exibição 1"
msg.attachments[1].display_name = "Novo nome de exibição 2"
```