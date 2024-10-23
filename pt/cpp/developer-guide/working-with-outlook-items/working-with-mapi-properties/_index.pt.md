---
title: "Trabalhando com Propriedades MAPI usando a Biblioteca Email C++"
description: "Usando a API da Biblioteca de Email C++, você pode acessar e definir propriedades MAPI do Outlook e ler Propriedades MAPI Nomeadas de arquivos MSG."
url: /pt/cpp/trabalhando-com-propriedades-mapi/
weight: 60
type: docs
linktitle: "Trabalhando com Propriedades MAPI"
---

## **Acessando e Definindo Propriedade MAPI do Outlook**
A classe MapiProperty representa uma propriedade MAPI, que contém:

- Nome: uma string que representa o nome da propriedade.
- Tag: um long que representa a tag da propriedade.
- Dados: um array de bytes que representa os dados da propriedade.

### **Obter Propriedade MAPI usando a Tag de Propriedade MAPI**
Para obter propriedades MAPI:

1. Crie uma instância de MapiMessage carregando de arquivos ou stream.
1. Obtenha a MapiProperty de MapiMessage.Properties pelas chaves MapiPropertyTag.
1. Obtenha os Dados da MapiProperty pelo método GetX.

O seguinte trecho de código mostra como obter a propriedade MAPI usando a tag de propriedade MAPI com a Biblioteca de Parser de Email C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Definindo Propriedades MAPI**
O seguinte trecho de código mostra como definir propriedades MAPI.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

onde a definição do método convertDateTime é a seguinte:

``` java

 int64_t filetime = t.ToFileTime();

System::ArrayPtr<uint8_t> d = System::MakeArray<uint8_t>(8, 0);

d[0] = (uint8_t)(filetime & 0xFF);

d[1] = (uint8_t)((filetime & 0xFF00) >> 8);

d[2] = (uint8_t)((filetime & 0xFF0000) >> 16);

d[3] = (uint8_t)((filetime & 0xFF000000) >> 24);

d[4] = (uint8_t)((filetime & 0xFF00000000) >> 32);

d[5] = (uint8_t)((filetime & 0xFF0000000000) >> 40);

d[6] = (uint8_t)((filetime & 0xFF000000000000) >> 48);

d[7] = (uint8_t)(((uint64_t)filetime & 0xFF00000000000000) >> 56);

```

## **Lendo Propriedades MAPI Nomeadas de Arquivos MSG do Outlook**
O Microsoft Outlook suporta a adição de propriedades MAPI nomeadas a um arquivo MSG. Essas propriedades MAPI nomeadas são adicionadas pelo usuário. Você pode adicionar uma propriedade nomeada, por exemplo “MyProp”, a um arquivo MSG usando Aspose.Email. Este artigo ilustra as capacidades do Aspose.Email para:

- Ler Propriedades MAPI Nomeadas de um arquivo MSG do Outlook
- Ler Propriedades de Anexos
- Remover Propriedades de MSGs e Anexos

### **Ler Propriedades MAPI Nomeadas de arquivo MSG**
O seguinte trecho de código mostra como ler propriedades MAPI nomeadas de um arquivo MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Lendo Propriedade MAPI Nomeada de Anexo**
Aspose.Email também permite que você navegue pelas propriedades de um MapiAttachment e busque por uma propriedade nomeada, de forma similar ao exemplo acima, para MapiMessage. O seguinte trecho de código mostra como buscar por uma propriedade nomeada através da coleção de propriedades do anexo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Remover Propriedades de MSGs e Anexos**
O seguinte trecho de código mostra como remover propriedades de MSGs e anexos.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}