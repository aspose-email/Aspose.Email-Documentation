---
title: "Trabalhando com Propriedades MAPI"
url: /pt/python-net/trabalhando-com-propriedades-mapi/
weight: 60
type: docs
---


## **Acessando e Definindo Propriedades MAPI do Outlook**

A classe MapiProperty representa uma propriedade MAPI, que contém:

- Nome: uma string que representa o nome da propriedade.
- Tag: um longo que representa a tag da propriedade.
- Dados: um array de bytes que representa os dados da propriedade.

### **Obtendo Propriedade MAPI usando a Tag da Propriedade MAPI**

Para obter propriedades MAPI:

1. Crie uma instância de MapiMessage carregando de arquivos ou stream.
1. Obtenha a MapiProperty de MapiMessage.Properties pelas chaves MapiPropertyTag.
1. Obtenha os Dados da MapiProperty pelo método GetX.

O seguinte trecho de código mostra como obter a propriedade MAPI usando a tag da propriedade MAPI.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Definindo Propriedades MAPI**

O seguinte trecho de código mostra como definir propriedades MAPI.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}

onde a definição do método convertDateTime é a seguinte:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Lendo Propriedades Nomeadas MAPI de Arquivos MSG do Outlook**

Aspose.Email fornece um conjunto de APIs para trabalhar com arquivos MSG, incluindo a extração de propriedades MAPI nomeadas.

### **Ler Propriedades MAPI Nomeadas de um arquivo MSG**

Para ler propriedades MAPI nomeadas, podemos usar a propriedade **named_properties** da classe [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class). O seguinte exemplo de código mostra como carregar uma mensagem, recuperar todas as propriedades MAPI nomeadas, iterar sobre cada propriedade para verificar seu valor:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Obter todas as propriedades MAPI nomeadas
properties = msg.named_properties.values
# Ler todas as propriedades em um loop foreach
for prop in properties:
    #  Ler qualquer propriedade específica
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Lendo Propriedade MAPI Nomeada de Anexos**

Aspose.Email possibilita a recuperação de todas as propriedades MAPI nomeadas de um anexo. O seguinte exemplo de código mostra como ler propriedades MAPI nomeadas de anexos:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Obter todas as propriedades MAPI nomeadas
attach_properties = msg.attachments[0].named_properties.values
# Ler todas as propriedades em um loop foreach
for prop in attach_properties:
    #  Ler qualquer propriedade específica
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Remover Propriedades de MSGs e Anexos**

Este exemplo de código demonstra a criação de uma mensagem MSG do Outlook com um conteúdo de corpo e um arquivo de mensagem anexado. Também mostra como excluir uma propriedade de anexo da mensagem criada.

```python
import aspose.email as ae

# criar um MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>Este é o conteúdo do corpo</h1></body></html>", ae.mapi.BodyContentType.HTML)

# carregar mensagem e adicioná-la ao MSG criado como anexo
attachment = ae.mapi.MapiMessage.load("attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# contagem de propriedades de anexo antes da remoção
print(f"Antes da remoção = {msg.attachments[0].properties.count}")

# Excluir qualquer propriedade de anexo
msg.attachments[0].remove_property(923467779)

# contagem de propriedades de anexo após a remoção
print(f"Após a remoção = {msg.attachments[0].properties.count}")
```