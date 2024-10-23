---
title: "Trabalhando com Anexos de Mensagem"
url: /pt/net/trabalhando-com-anexos-de-mensagem/
weight: 80
type: docs
---


## **Gerenciando Anexos com Aspose Outlook**

[Creating and Saving Outlook Message (MSG) Files](https://docs.aspose.com/email/pt/net/creating-and-saving-msg-files/) explica como criar e salvar mensagens, e como criar arquivos MSG com anexos. Este artigo explica como gerenciar anexos do Microsoft Outlook com Aspose.Email. Anexos de um arquivo de mensagem são acessados e salvos em disco usando a propriedade [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). A propriedade [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) é uma coleção do tipo [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/).

### **Verificar se o Anexo é Inline ou Regular**

Anexos inline e regulares servem para propósitos diferentes. Anexos inline estão visualmente integrados à mensagem de e-mail e geralmente são imagens ou arquivos de mídia. Enquanto isso, anexos regulares são arquivos separados anexados ao e-mail e podem incluir vários tipos de arquivos. A propriedade [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) da classe [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) recebe um valor que indica se o anexo é inline ou regular.

O seguinte exemplo de código extrai e exibe informações sobre cada anexo na MapiMessage carregada, incluindo seus nomes de exibição e se são anexos inline ou não.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Salvar Anexos do Arquivo de Mensagem (MSG) do Outlook**

Para salvar anexos de um arquivo MSG:

1. Itere pela coleção [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) e obtenha os anexos individuais.
1. Para salvar os anexos, chame o método Save() da classe MapiAttachment.

O seguinte trecho de código mostra como salvar anexos no disco local.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Obtendo Anexos de Mensagens de E-mail Aninhadas**

Anexos OLE incorporados também aparecem na coleção de Anexos da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). O seguinte exemplo de código analisa um arquivo de mensagem em busca de anexos de mensagem incorporados e os salva no disco. O método estático FromProperties() da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) pode criar uma nova mensagem a partir de um anexo incorporado. O seguinte trecho de código mostra como obter anexos de mensagens de e-mail aninhadas.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Removendo Anexos**

A biblioteca Aspose Outlook fornece a funcionalidade para remover anexos de arquivos Microsoft Outlook Message (.msg):

- Chame o método RemoveAttachments(). Ele recebe o caminho do arquivo de mensagem como um parâmetro. É implementado como um método público e estático, portanto, você não precisa instanciar o objeto.

O seguinte trecho de código mostra como remover anexos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

Você também pode chamar o método estático [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). Ele funciona mais rápido que RemoveAttachment(), porque o método RemoveAttachment() analisa o arquivo de mensagem.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Adicionando Anexos MSG**

Uma mensagem do Outlook pode conter outras mensagens do Microsoft Outlook em anexos, seja como mensagens regulares ou incorporadas. A [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) fornece membros sobrecarregados do método Add para criar mensagens do Outlook com ambos os tipos de anexos.

{{% alert %}}
**Experimente!**

Adicione ou remova anexos de e-mail com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}

### **Adicionando um ReferenceAttachment em um MapiMessage**

O método [MapiAttachmentCollection.Add(string name, string sharedLink, string url, string providerName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) da classe [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) permite adicionar um anexo de referência em um MapiMessage. Quando os destinatários do e-mail clicam no anexo de referência, eles poderão acessar o arquivo vinculado se tiverem as permissões apropriadas para fazê-lo. Usando um anexo de referência, você pode enviar uma mensagem de e-mail menor e garantir que todos tenham acesso à versão mais atualizada do arquivo ou item.

O método possui os seguintes parâmetros:

- *name* - o nome do anexo
- *sharedLink* - um link compartilhado totalmente qualificado para o anexo fornecido pelo serviço web que manipula o anexo
- *url* - uma localização de arquivo
- *providerName* - um nome do provedor de anexo de referência

O exemplo de código abaixo demonstra como adicionar um anexo de referência a uma mensagem:

```cs
// Suponha que você queira enviar uma mensagem de e-mail que inclua um link para um arquivo Document.pdf armazenado no Google Drive.
// Em vez de anexar o documento diretamente à mensagem de e-mail,
// você pode criar um anexo de referência que vincula ao arquivo no Google Drive.

// Crie uma mensagem
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Arquivo de mensagem do Outlook",
    "Esta mensagem é criada pela Aspose.Email", OutlookMessageFormat.Unicode);

// Adicione um anexo de referência
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
// Você também pode definir propriedades adicionais do anexo
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Por fim, salve a mensagem
msg.Save(@"my.msg");
```

### **Incorporando uma Mensagem como Anexo**

O seguinte trecho de código mostra como incorporar um anexo de arquivo MSG a uma mensagem.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Lendo Mensagens Incorporadas de Anexos**

O seguinte trecho de código mostra como ler mensagens incorporadas de anexos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Inserção e Substituição de Anexos**

A API Aspose.Email fornece a capacidade de inserir anexos em um índice específico na mensagem pai. Também fornece a capacidade de substituir o conteúdo de um anexo por outro anexo de mensagem.

{{% alert %}}
**Experimente!**

Execute o projeto simples [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach), e experimente as capacidades da Aspose.Email para substituir anexos em ação.
{{% /alert %}} 

### **Inserir em Localização Específica**

A API Aspose.Email fornece a capacidade de inserir um anexo MSG em um MSG pai usando o método Insert da MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). O seguinte trecho de código mostra como inserir um anexo em uma localização específica.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Substituir Conteúdos de Anexo**

Isso pode ser usado para substituir os conteúdos de um anexo incorporado pelos novos usando o método Replace. No entanto, não pode ser usado para inserir um anexo com PR_ATTACH_NUM = 4 (por exemplo) na coleção com collection.Count = 2. O seguinte trecho de código mostra como substituir os conteúdos de um anexo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Renomeando um Anexo em MapiMessage**

É possível editar o valor da propriedade DisplayName nos anexos de MapiMessage.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "Novo nome de exibição 1";
msg.Attachments[1].DisplayName = "Novo nome de exibição 2";
```

## **Salvar Anexos de Mensagens Digitalmente Assinadas**

A API Aspose.Email fornece a capacidade de obter ou definir um valor indicando se a mensagem assinada em claro será decodificada.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}