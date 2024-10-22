---
title: "Trabalhando com Contatos do Outlook"
url: /pt/net/trabalhando-com-contatos-do-outlook/
weight: 90
type: docs
---


## **Criando, Salvando e Lendo Contatos**

Assim como o MapiMessage, o Aspose.Email permite que você crie contatos do Outlook. A classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) fornece todas as propriedades relacionadas ao contato necessárias para criar um contato do Outlook. Este artigo mostra como criar, salvar e ler um contato do Outlook usando a classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

### **Criar e Salvar Contato do Outlook**

Para criar um contato e salvá-lo no disco:

1. Instancie um novo objeto da classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Insira as informações da propriedade do contato.
1. Adicione os dados da foto (se houver).
1. Salve o contato no formato MSG ou VCard.

O seguinte trecho de código mostra como criar e salvar um contato do Outlook.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Salvar Lista de Distribuição Mapi em um Único Arquivo VCF de Múltiplos Contatos**

O exemplo de código abaixo demonstra como salvar uma lista de distribuição em um arquivo VCF de múltiplos contatos:

```cs
// converte o objeto `msg` para um objeto `MapiMessage`
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//salvar a lista de distribuição
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```


### **Salvar Contato no Formato VCF versão 3**

Para salvar o contato no formato VCF versão 3, use o enumerador [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) para definir a propriedade [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/). O seguinte código de amostra demonstra o uso do [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerador para salvar o contato no formato VCF versão 3:

```cs

```

### **Lendo um MapiContact**

A classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) pode ser usada para carregar contatos do Outlook nos formatos MSG e VCard. O seguinte trecho de código mostra como carregar contatos do Outlook salvos como MSG e VCF em um [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Carregando um Contato de MSG**

O seguinte trecho de código mostra como carregar contatos de MSG.

#### **Carregando um Contato de VCard**

O seguinte trecho de código mostra como carregar contatos de VCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Carregando um Contato de VCard com Codificação Especificada**

O seguinte trecho de código mostra como carregar contatos de VCard com a codificação especificada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Salvando Itens de Contato VCard com Codificação Especificada**

Personalize o comportamento de salvamento ao trabalhar com arquivos VCard usando a classe [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). A propriedade [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) da classe especificará a codificação a ser usada ao salvar itens de contato VCard.

O seguinte exemplo de código mostra como implementar essa propriedade em seu projeto:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Salvando Arquivos VCard com Campos Estendidos**

A propriedade [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) permite controlar se campos estendidos podem ser usados ao salvar arquivos vCard. Quando definida como verdadeira (padrão), extensões são permitidas, proporcionando compatibilidade com campos personalizados e informações adicionais de contato.

### **Lendo Múltiplos Contatos em formato VCard**

Nossa biblioteca torna possível obter a lista de todos os contatos de um VCard. Isso pode ser feito usando os seguintes métodos e etapas:

```cs
// Verifica se o fluxo de origem VCard contém múltiplos contatos.
VCardContact.IsMultiContacts(Stream stream)

// Carrega a lista de todos os contatos do arquivo VCard.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Carrega a lista de todos os contatos do fluxo VCard.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
O seguinte trecho de código demonstra como lidar com arquivos VCard que contêm múltiplos contatos:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

## **Renderizando Informações de Contato para MHTML**

Contatos do Outlook podem ser convertidos para MHTML usando a API Aspose.Email. Este exemplo mostra como um VCard é carregado em [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) e, em seguida, convertido para MHTML com a ajuda da API [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}