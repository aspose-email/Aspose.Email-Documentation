---
title: "Trabalhando com Propriedades MAPI"
url: /pt/net/trabalhando-com-propriedades-mapi/
weight: 70
type: docs
---


## **Acessando e Definindo Propriedade MAPI do Outlook**

A classe [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) representa uma propriedade MAPI, que contém:

- [Nome](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): uma string que representa a propriedade do nome.
- [Tag](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): um valor do tipo longo que representa a propriedade da tag.
- [Dados](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): um array de bytes que representa a propriedade de dados.
  
### **Obtendo Propriedade MAPI usando a Tag de Propriedade MAPI**

Para obter propriedades MAPI:

1. Crie uma instância de [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) por [carregando de arquivos ou stream](https://docs.aspose.com/email/pt/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Obtenha a [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) de [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) usando as chaves de [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/).

O seguinte trecho de código mostra como obter a propriedade MAPI usando a tag da propriedade MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Definindo Propriedades MAPI**

O seguinte trecho de código mostra como definir propriedades MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

onde a definição do método convertDateTime é a seguinte:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Algumas Propriedades Adicionais**

O seguinte trecho de código mostra como definir propriedades MAPI adicionais.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Lendo Propriedades MAPI Nomeadas de Arquivos MSG do Outlook**

O Microsoft Outlook suporta a adição de propriedades MAPI nomeadas a um arquivo MSG. Essas propriedades MAPI nomeadas são adicionadas pelo usuário. Você pode adicionar uma propriedade nomeada, por exemplo, “MyProp”, a um arquivo MSG usando Aspose.Email. Este artigo ilustra as capacidades do Aspose.Email para:

- [**Acessando e Definindo Propriedade MAPI do Outlook**](#acessando-e-definindo-propriedade-mapi-do-outlook)
  - [**Obtendo Propriedade MAPI usando a Tag de Propriedade MAPI**](#obtendo-propriedade-mapi-usando-a-tag-de-propriedade-mapi)
  - [**Definindo Propriedades MAPI**](#definindo-propriedades-mapi)
  - [**Algumas Propriedades Adicionais**](#algumas-propriedades-adicionais)
- [**Lendo Propriedades MAPI Nomeadas de Arquivos MSG do Outlook**](#lendo-propriedades-mapi-nomeadas-de-arquivos-msg-do-outlook)
  - [**Ler Propriedades MAPI Nomeadas de arquivo MSG**](#ler-propriedades-mapi-nomeadas-de-arquivo-msg)
  - [**Lendo Propriedade MAPI Nomeada de Anexo**](#lendo-propriedade-mapi-nomeada-de-anexo)
  - [**Remover Propriedades de MSGs e Anexos**](#remover-propriedades-de-msgs-e-anexos)
  
### **Ler Propriedades MAPI Nomeadas de arquivo MSG**

O seguinte trecho de código mostra como ler propriedades MAPI nomeadas do arquivo MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Lendo Propriedade MAPI Nomeada de Anexo**

Aspose.Email também permite que você percorra as propriedades de um [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) e busque uma propriedade nomeada, de forma semelhante ao exemplo acima, para [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). O seguinte trecho de código mostra como buscar uma propriedade nomeada através da coleção de propriedades do anexo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Remover Propriedades de MSGs e Anexos**

O seguinte trecho de código mostra como remover propriedades de MSGs e anexos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}