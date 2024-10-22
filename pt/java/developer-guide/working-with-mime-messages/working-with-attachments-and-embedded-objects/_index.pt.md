---
title: "Trabalhando com Anexos e Objetos Embutidos"
url: /pt/java/trabalhando-com-anexos-e-objetos-embutidos/
weight: 20
type: docs
---


## **Gerenciando Anexos de Email**

Um anexo de email é um arquivo que é enviado junto com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. A classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) é usada com a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//). Todas as mensagens incluem um corpo. Além do corpo, você pode querer enviar arquivos adicionais. Esses são enviados como anexos e representam uma instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//). Você pode enviar qualquer número de anexos, mas o tamanho do anexo é limitado pelo servidor de email. O Gmail, por exemplo, não suporta tamanhos de arquivo superiores a 10MB.
{{% alert %}}
**Experimente!**

Adicione ou remova anexos de email online com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}

### **Adicionando Anexo**

Para anexar um anexo a um email, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Crie uma instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
1. Carregue o anexo na instância da [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) .
1. Adicione a instância da [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) à instância da [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

O seguinte trecho de código mostra como adicionar um anexo a uma mensagem de email.

```java
// Crie uma instância da classe MailMessage
MailMessage message = new MailMessage();
message.setFrom(new MailAddress("sender@from.com"));
message.getTo().add("receiver@to.com");
message.setSubject("Esta é uma mensagem");
message.setBody("Este é o corpo");

// Carregue um anexo
Attachment attachment = new Attachment("1.txt");

// Adicione Múltiplos Anexos na instância da classe MailMessage e salve a mensagem no disco
message.getAttachments().addItem(attachment);
message.addAttachment(new Attachment("1.jpg"));
message.addAttachment(new Attachment("1.doc"));
message.addAttachment(new Attachment("1.rar"));
message.addAttachment(new Attachment("1.pdf"));
message.save("AddAttachments.eml");
```

Acima, descrevemos como adicionar anexos à sua mensagem de email com Aspose.Email. O que segue mostra como remover anexos e exibir informações sobre eles na tela.

### **Removendo um Anexo**

Para remover um anexo, siga as etapas a seguir:

- Crie uma instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Carregue o anexo na instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Adicione o anexo à instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Remova os anexos da instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) usando a instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

O seguinte trecho de código mostra como remover um anexo.

```java
// Crie uma instância da classe MailMessage
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Carregue um anexo
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Remova o anexo do seu MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Exibindo Nome do Arquivo do Anexo**

Para exibir o nome do arquivo do anexo, siga estas etapas:

1. Percorra os anexos na mensagem de email e
   1. Salve cada anexo.
   1. Exiba cada nome de anexo na tela.

O seguinte trecho de código mostra como exibir um nome de arquivo de anexo na tela.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Exiba o nome do arquivo do anexo
    System.out.println(attachment.getName());
}
```

### **Extraindo Anexos de Email**

Este tópico explica como extrair um anexo de um arquivo de email. Um anexo de email é um arquivo que é enviado junto com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. Todas as mensagens de email incluem uma opção para enviar arquivos adicionais. Esses são enviados como anexos e são representados como instâncias da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/). A classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) é usada com a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) para trabalhar com anexos. Para extrair anexos de uma mensagem de email, siga estas etapas:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Carregue um arquivo de email na instância da [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Crie uma instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) e use-a em um loop para extrair todos os anexos.
- Salve o anexo e exiba-o na tela.

|**Anexos extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
O seguinte trecho de código mostra como Extrair Anexos de Email.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Recuperando Content-Description do Anexo**

A API Aspose.Email fornece a capacidade de ler a Content-Description do anexo a partir do cabeçalho do anexo. O seguinte trecho de código mostra como recuperar a descrição do conteúdo do anexo.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Determinando se um Anexo é uma Mensagem Embutida**

O seguinte trecho de código demonstra como determinar se o anexo é uma mensagem embutida ou não.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "O anexo é uma mensagem embutida."
        : "O anexo não é uma mensagem embutida.");
```
#### **Determinar Anexos Formatados TNEF**

A propriedade [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) da API Aspose.Email Java indica se o anexo da mensagem é uma mensagem formatada TNEF.

O seguinte trecho de código demonstra como determinar se um anexo é formatado TNEF:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("O Anexo é TNEF?: " + attachment.isTnef());
}
```

#### **Extraindo URI do Anexo se o Anexo for URI-anexo**

O seguinte trecho de código demonstra como extrair a URI do Anexo.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("URI do Anexo: " + uri);
}
~~~

### **Adicionando Anexos de Referência**

Um anexo de referência é uma alternativa ao anexo de arquivo local. Em alguns casos, anexos de referência podem ser preferíveis, por exemplo, se você desejar gerenciar seu acesso. As classes abaixo são usadas para gerenciar e manipular mensagens de email e seus anexos:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - Representa um anexo de referência. 
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - O tipo de permissão de dados associado a um anexo de referência da web. 
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - O tipo de serviço da web que manipula o anexo.

O seguinte exemplo de código demonstra como carregar uma mensagem de email de um arquivo, criar um anexo de referência com propriedades específicas e adicionar o anexo à mensagem de email:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]");
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Trabalhando com Objetos Embutidos**

Um objeto embutido é um objeto que foi criado com uma aplicação e encerrado dentro de um documento ou arquivo criado por outra aplicação. Por exemplo, uma planilha do Microsoft Excel pode ser embutida em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser embutido em uma apresentação do Microsoft PowerPoint. Quando um arquivo está embutido, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento embutido pode ser aberto na aplicação original e modificado.

### **Incorporando Objetos em um Email**

A classe [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) é usada com a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) para incorporar objetos em suas mensagens de email. Para adicionar um objeto embutido, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique os valores de de, para e assunto na instância da [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Crie uma instância da classe [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/).
1. Crie uma instância da classe [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/).
1. Carregue um objeto embutido na [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Adicione o objeto embutido carregado à instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Adicione a instância [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) à instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Os trechos de código abaixo produzem uma mensagem de email com corpo de texto simples e HTML e uma imagem embutida no HTML.

|**Imagem embutida no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Você pode enviar qualquer número de objetos embutidos. O tamanho do anexo é limitado pelo servidor de email. O Gmail, por exemplo, não suporta tamanhos de arquivo superiores a 10MB. Os trechos de código abaixo demonstram como embutir objetos em um Email.

```java
// Crie uma instância da classe MailMessage e defina os endereços e o conteúdo
MailMessage mail = new MailMessage();
mail.setFrom(new MailAddress("sender@from.com"));
mail.getTo().add("receiver@to.com");
mail.setSubject("Este é um email");

// Crie a parte de texto simples. É visível para aqueles clientes que não suportam HTML
AlternateView plainView = AlternateView.createAlternateViewFromString("Este é meu conteúdo de texto simples", null, "text/plain");

// Crie a parte HTML. Para embutir imagens, precisamos usar o prefixo 'cid' no valor do src da img.
// O valor cid será mapeado para o Content-Id de um recurso vinculado.
// Assim <img src='cid:barcode'> será mapeado para um LinkedResource com um ContentId de //'barcode'.
AlternateView htmlView = AlternateView.createAlternateViewFromString("Aqui está uma imagem embutida.<img src=cid:barcode>", null, "text/html");

// Crie o LinkedResource (imagem embutida) e adicione o LinkedResource à visualização apropriada
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Removendo Objetos Embutidos do Email**

A [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) é acessada através da propriedade [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--). A coleção [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) fornece um método para remover completamente objetos embutidos adicionados a uma mensagem de email. Use a versão sobrecarregada do método [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) para remover todos os vestígios de um objeto embutido de uma mensagem de email.

O código de exemplo abaixo mostra como remover objetos embutidos de uma mensagem de email.

```java
// Carregue a mensagem de teste com Recursos Vinculados
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Remova um LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Agora limpe a Visualização Alternativa para recursos vinculados
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Extraindo Objetos Embutidos**

Este tópico explica como extrair objetos embutidos de um arquivo de email. Um objeto embutido é um objeto que foi criado com uma aplicação e encerrado dentro de um documento ou arquivo criado por outra aplicação. Por exemplo, uma planilha do Microsoft Excel pode ser embutida em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser embutido em uma apresentação do Microsoft PowerPoint. Quando um arquivo está embutido, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento embutido pode ser aberto na aplicação original e ser modificado. Para extrair um objeto embutido de uma mensagem de email, siga estas etapas:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Carregue um arquivo de email na instância da [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Crie um loop e crie uma instância da classe [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) nela.
1. Salve o anexo e exiba-o na tela.
1. Especifique o endereço do remetente e do destinatário na instância da [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Envie o email usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

O trecho de código abaixo extrai objetos embutidos de um email.

|**Objetos embutidos extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
O seguinte trecho de código mostra como extrair objetos embutidos.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Identificar e Extrair um anexo embutido de MSG formatado como RTF**

O seguinte código pode ser usado para mensagens formatadas como RTF para diferenciar e extrair anexos que estão Inline ou aparecem como Ícone no corpo da mensagem. O seguinte trecho de código mostra como identificar e extrair um anexo embutido de MSG formatado como RTF.

```java
public static void extractInlineAttachments() {
    MapiMessage message = MapiMessage.load("MSG file with RTF Formatting.msg");
    for (MapiAttachment attachment : message.getAttachments()) {

        if (isAttachmentInline(attachment)) {
            try {
                saveAttachment(attachment, UUID.randomUUID().toString());
            } catch (Exception ex) {
                System.err.println(ex);
            }
        }
    }
}

static boolean isAttachmentInline(MapiAttachment attachment) {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("\u0003ObjInfo".equals(property.getName())) {
            byte[] data = property.getData();
            int odtPersist1 = data[1] << 8 | data[0];
            return (odtPersist1 & 0x40) == 0;
        }
    }
    return false;
}

static void saveAttachment(MapiAttachment attachment, String fileName) throws IOException {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("Package".equals(property.getName())) {
            try (FileOutputStream fs = new FileOutputStream(fileName)) {
                fs.write(property.getData(), 0, property.getData().length);
            }
        }
    }
}
```

## **Recuperando Anexos de Email Assinado**

Emails assinados contêm um único anexo **smime.p7m**. Isso significa que o email é criptografado por SMIME.
O formato de arquivo **Smime.p7m** é a assinatura digital.
Para ver o conteúdo deste email, use o método [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). O método retorna um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) sem uma assinatura digital.

```java
MailMessage signedEml = MailMessage.load("signed.eml");

if (signedEml.isSigned()) {
    for (int i = 0; i < signedEml.getAttachments().size(); i++) {
        System.out.println("Anexo de email assinado" + i + ": " + signedEml.getAttachments().get_Item(i).getName());
    }

    // O email está assinado. Remova a assinatura.
    MailMessage eml = signedEml.removeSignature();

    System.out.println("Assinatura removida.");

    for (int i = 0; i < eml.getAttachments().size(); i++) {
        System.out.println("Anexo do email" + i + ": " + eml.getAttachments().get_Item(i).getName());
    }
}
```

### **Trabalhando com Content-Type e Content-Disposition**

A API Aspose.Email fornece a capacidade de trabalhar com o [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) do anexo e o [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) do cabeçalho do anexo. O seguinte trecho de código mostra como obter e alterar a descrição do conteúdo a partir do anexo.

#### **Exibindo parâmetros Content-Type e Content-Disposition**

O seguinte trecho de código mostra como exibir os parâmetros de Content-Type e Content-Disposition na tela:

~~~Java
void run(MailMessage message) {
    // Anexos
    for (Attachment attachment : message.getAttachments()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
    // Recursos Vinculados
    for (LinkedResource attachment : message.getLinkedResources()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
}

void printContentType(ContentType contentType) {
    System.out.println("media-type: " + contentType.getMediaType());
    System.out.println("charset: " + contentType.getCharSet());
    System.out.println("name: " + contentType.getName());
}

void printContentDisposition(ContentDisposition contentDisposition) {
    System.out.println("disposition-type: " + contentDisposition.getDispositionType());
    System.out.println("is-inline: " + contentDisposition.getInline());
    System.out.println("filename: " + contentDisposition.getFileName());
    System.out.println("creation-date: " + contentDisposition.getCreationDate());
    System.out.println("modification-date: " + contentDisposition.getModificationDate());
    System.out.println("read-date: " + contentDisposition.getReadDate());
    System.out.println("size: " + contentDisposition.getSize());
}
~~~ 

#### **Usando parâmetros Content-Type e Content-Disposition com Anexos**

O seguinte trecho de código mostra como usar os parâmetros Content-Type e Content-Disposition com um anexo:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~