---
title: "Trabalhando com Anexos e Objetos Embutidos"
url: /pt/net/trabalhando-com-anexos-e-objetos-embutidos/
weight: 20
type: docs
---

## **Gerenciando Anexos de Email**

Um anexo de email é um arquivo que é enviado juntamente com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, além de ser parte da mensagem à qual está anexado. A classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) é utilizada com a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Todas as mensagens incluem um corpo. Além do corpo, você pode querer enviar arquivos adicionais. Estes são enviados como anexos e são representados como uma instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). Você pode enviar qualquer número de anexos, mas o tamanho do anexo é limitado pelo servidor de email. O Gmail, por exemplo, não suporta tamanhos de arquivos maiores que 10MB.
{{% alert %}}
**Experimente!**

Adicione ou remova anexos de email online com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}

### **Adicionando um Anexo**

Para adicionar um anexo a um email, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Crie uma instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
1. Carregue o anexo na instância [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
1. Adicione a instância [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) à instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

O código abaixo mostra como adicionar um anexo a uma mensagem de email.

```csharp
// Crie uma instância da classe MailMessage
var eml = new MailMessage
{
    From = "sender@from.com",
    To = "receiver@to.com",
    Subject = "Esta é uma mensagem",
    Body = "Este é o corpo"
};

// Carregue um anexo
var attachment = new Attachment("1.txt");

// Adicione múltiplos anexos à instância da classe MailMessage e salve a mensagem em disco
eml.Attachments.Add(attachment);

eml.AddAttachment(new Attachment("1.jpg"));
eml.AddAttachment(new Attachment("1.doc"));
eml.AddAttachment(new Attachment("1.rar"));
eml.AddAttachment(new Attachment("1.pdf"));
eml.Save("AddAttachments.eml");
```

Acima, descrevemos como adicionar anexos à sua mensagem de email com Aspose.Email. O que segue mostra como remover anexos e exibir informações sobre eles na tela.

### **Adicionando um Anexo de Referência**

Um anexo de referência é um tipo de anexo que inclui um link ou uma referência a um arquivo ou item, em vez de incluir o próprio arquivo ou item na mensagem de email. Quando os destinatários do email clicam no anexo de referência, eles poderão acessar o arquivo vinculado se tiverem as permissões apropriadas para isso. Usando um anexo de referência, você pode enviar uma mensagem de email menor e garantir que todos tenham acesso à versão mais atualizada do arquivo ou item.

O código abaixo mostra como adicionar um anexo de referência a um email. O código realiza as seguintes etapas:

1. Carrega o arquivo da mensagem de email usando o método [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Cria um novo objeto ReferenceAttachment chamado refAttach, passando a URL do anexo "https://[attach_uri]" como parâmetro para seu construtor.
3. Define o nome do anexo como "Document.docx" usando a propriedade [Name](https://reference.aspose.com/email/net/aspose.email/attachment/name/) do objeto refAttach.
4. Define o tipo de provedor do anexo como [AttachmentProviderType.OneDrivePro](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) usando a propriedade [ProviderType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/providertype/) do objeto refAttach.
5. Define o tipo de permissão do anexo como [AttachmentPermissionType.AnyoneCanEdit](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) usando a propriedade [PermissionType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/permissiontype/) do objeto refAttach.
6. Adiciona o objeto refAttach à coleção [Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) do objeto eml usando o método [Add()](https://reference.aspose.com/email/net/aspose.email/attachmentcollection/).

```cs
var eml = MailMessage.Load("fileName");

var refAttach = new ReferenceAttachment("https://[attach_uri]")
{
    Name = "Document.docx",
    ProviderType = AttachmentProviderType.OneDrivePro,
    PermissionType = AttachmentPermissionType.AnyoneCanEdit
};

eml.Attachments.Add(refAttach);
```

### **Removendo um Anexo**

Para remover um anexo, siga as etapas abaixo:

- Crie uma instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Carregue o anexo na instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Adicione o anexo à instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Remova os anexos da instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) usando a instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

O código abaixo mostra como remover um anexo.

```csharp
// Crie uma instância da classe MailMessage
var eml = new MailMessage {From = "sender@sender.com", To = "receiver@gmail.com"};

// Carregue um anexo
var attachment = new Attachment("1.txt");
eml.Attachments.Add(attachment);

// Remova o anexo da sua MailMessage
eml.Attachments.Remove(attachment);
```

### **Exibindo o Nome do Arquivo do Anexo**

Para exibir o nome do arquivo de um anexo, siga estas etapas:

1. Percorra os anexos na mensagem de email e salve cada anexo.
2. Exiba cada nome de anexo na tela.

O código abaixo mostra como exibir o nome de um arquivo de anexo na tela.

```csharp
var eml = MailMessage.Load("Attachments.eml");

foreach (var attachment in eml.Attachments)
{
    // Exibe o nome do arquivo do anexo
    Console.WriteLine(attachment.Name);
}
```

### **Extraindo Anexos de Email**

Este tópico explica como extrair um anexo de um arquivo de email. Um anexo de email é um arquivo que é enviado juntamente com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, além de ser parte da mensagem à qual está anexado. Todas as mensagens de email incluem uma opção para enviar arquivos adicionais. Estes são enviados como anexos e são representados como instâncias da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). A classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) é utilizada com a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para trabalhar com anexos. Para extrair anexos de uma mensagem de email, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Carregue um arquivo de email na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Crie uma instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) e utilize-a em um loop para extrair todos os anexos.
- Salve o anexo e exiba-o na tela.

|**Anexos extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
O código abaixo mostra como extrair anexos de email.

```csharp
var eml = MailMessage.Load("Message.eml", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.eml");
    Console.WriteLine(attachment.Name);
}
```

#### **Recuperando Content-Description do Anexo**

A API Aspose.Email fornece a capacidade de ler uma Content-Description de um anexo no cabeçalho do anexo. O código abaixo mostra como recuperar a descrição de conteúdo do anexo.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");
Console.WriteLine(eml.Attachments[0].Headers["Content-Description"]);
```

#### **Determinando se o Anexo é uma Mensagem Embutida**

O código abaixo demonstra como determinar se o anexo é uma mensagem embutida ou não.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");

Console.WriteLine(eml.Attachments[0].IsEmbeddedMessage
    ? "O anexo é uma mensagem embutida."
    : "O anexo não é uma mensagem embutida.");
```

## **Trabalhando com imagens embutidas**

### **Adicionar imagem embutida ao corpo do email**

A classe [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) é usada com a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) para embutir objetos em sua mensagem de email. Para adicionar um objeto embutido, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Especifique os valores de de, para e assunto na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Crie uma instância da classe [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview).
1. Crie uma instância da classe [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/).
1. Carregue um objeto embutido na [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/).
1. Adicione o objeto embutido carregado à instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Adicione a instância [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) à instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Os códigos abaixo produzem uma mensagem de email com partes de texto simples e HTML e uma imagem embutida no HTML.

|**Imagem embutida no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Você pode enviar qualquer número de objetos embutidos. O tamanho do anexo é limitado pelo servidor de email. O Gmail, por exemplo, não suporta tamanhos de arquivos maiores que 10MB. Os códigos abaixo demonstram como embutir objetos em um Email.

```csharp
var eml = new MailMessage
{
    From = "AndrewIrwin@from.com",
    To = "SusanMarc@to.com",
    Subject = "Este é um email"
};

// Crie a parte de texto simples. É visível por aqueles clientes que não suportam HTML
var plainView =
    AlternateView.CreateAlternateViewFromString("Este é meu conteúdo em texto simples", null, "text/plain");

// Crie a parte HTML. Para embutir imagens, precisamos usar o prefixo 'cid' no valor src do img.
// O valor cid será mapeado para o Content-Id de um recurso vinculado. Assim <img src='cid:barcode'>
// será mapeado para um LinkedResource com um ContentId de 'barcode'.
var htmlView =
    AlternateView.CreateAlternateViewFromString("Aqui está uma imagem embutida.<img src=cid:barcode>", null,
        "text/html");

// Crie o LinkedResource (imagem embutida) e adicione o LinkedResource à visualização apropriada
var barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.Jpeg)
{
    ContentId = "barcode"
};

eml.LinkedResources.Add(barcode);
eml.AlternateViews.Add(plainView);
eml.AlternateViews.Add(htmlView);

eml.Save("EmbeddedImage_out.msg", SaveOptions.DefaultMsgUnicode);
```

### **Remover imagem embutida do corpo do email**

A [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) acessada através da propriedade [MailMessage.LinkedResources](https://reference.aspose.com/email/net/aspose.email/mailmessage/linkedresources/) fornece um método para remover completamente objetos embutidos adicionados em uma mensagem de email. Use a versão sobrecarregada do método [LinkedResourceCollection.RemoveAt](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/removeat/#removeat/) para remover todas as referências a um objeto embutido de uma mensagem de email.

O código de exemplo abaixo mostra como remover objetos embutidos de uma mensagem de email.

```csharp
// Carregue a mensagem de teste com Recursos Vinculados
var eml = MailMessage.Load("EmlWithLinkedResources.eml");

// Remova um LinkedResource
eml.LinkedResources.RemoveAt(0, true);

// Agora limpe a Visualização Alternativa para recursos vinculados
eml.AlternateViews[0].LinkedResources.Clear(true);
```

## **Trabalhando com Objetos Embutidos**

Um objeto embutido é um objeto que foi criado com um aplicativo e encerrado dentro de um documento ou arquivo criado por outro aplicativo. Por exemplo, uma planilha do Microsoft Excel pode ser embutida em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser embutido em uma apresentação do Microsoft PowerPoint. Quando um arquivo é embutido, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento embutido pode ser aberto no aplicativo original e modificado.

### **Extraindo Objetos Embutidos**

Este tópico explica como extrair objetos embutidos de um arquivo de email. O documento embutido pode ser aberto no aplicativo original e ser modificado. Para extrair um objeto embutido de uma mensagem de email, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Carregue um arquivo de email na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Crie um loop e crie uma instância da classe [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) nele.
1. Salve o anexo e exiba-o na tela.
1. Especifique o endereço do remetente e do destinatário na instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Envie o email usando a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

O código abaixo extrai objetos embutidos de um email.

|**Objetos embutidos extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
O código abaixo mostra como extrair objetos embutidos.

```csharp
var eml = MailMessage.Load("Message.msg", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.msg");
    Console.WriteLine(attachment.Name);
}
```

#### **Identificar e Extrair um anexo embutido de MSG formatado como RTF**

Para mensagens formatadas como RTF, o seguinte código pode ser usado para diferenciar e extrair anexos que são Inline ou aparecem como Ícone no corpo da mensagem. O código abaixo mostra como Identificar e Extrair um anexo embutido de MSG formatado como RTF.

```csharp
var eml = MapiMessage.Load("MSG file with RTF Formatting.msg");

foreach (var attachment in eml.Attachments)
{
    if (IsAttachmentInline(attachment))
    {
        try
        {
            SaveAttachment(attachment, Data.Out/new Guid().ToString());
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
}

static bool IsAttachmentInline(MapiAttachment attachment)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "\x0003ObjInfo")
        {
            var odtPersist1 = BitConverter.ToUInt16(property.Data, 0);
            return (odtPersist1 & (1 << (7 - 1))) == 0;
        }
    }
    return false;
}

static void SaveAttachment(MapiAttachment attachment, string fileName)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "Package")
        {
            using var fs = new FileStream(fileName, FileMode.Create, FileAccess.Write);
            fs.Write(property.Data, 0, property.Data.Length);
        }
    }
}
```

## **Recuperando Anexos de Email Assinado**

Emails assinados contêm um único anexo **smime.p7m**. Isso significa que o email está criptografado por SMIME. O formato de arquivo **smime.p7m** é a assinatura digital. Para ver o conteúdo deste email, use o método [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). O método retorna um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) sem uma assinatura digital.

```csharp
var signedEml = MailMessage.Load("signed.eml");
        
if (signedEml.IsSigned)
{
    for (var i = 0; i < signedEml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Anexo de email assinado{i}: {signedEml.Attachments[i].Name}");
    }
    
    // O email está assinado. Remover a assinatura.
    var eml = signedEml.RemoveSignature();
    
    Console.WriteLine(@"Assinatura removida.");

    for (var i = 0; i < eml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Anexo de email{i}: {eml.Attachments[i].Name}");
    }
}
```