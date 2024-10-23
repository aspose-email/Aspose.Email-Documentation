---
title: "Adicionar Imagens Incorporadas à Mensagem de Email no Aspose.Email"
url: /pt/java/add-embedded-images-to-email-message-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Adicionar Imagens Incorporadas à Mensagem de Email**
Com Aspose.Email, os desenvolvedores Java podem facilmente incorporar qualquer imagem em uma mensagem de email, além de anexá-la, conforme discutido em [Gerenciar Anexos na Mensagem de Email](/email/java/working-with-message-attachments). Para incorporar uma imagem, o Aspose.Email utiliza uma classe especializada, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Definir corpo Html. Também contém a tag <img> com cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>"

        + "<font color=blue>Esta linha está em azul</font><br><br>" +

        "Aqui está uma imagem incorporada.<img src=cid:companylogo>");

// Adicionar recurso vinculado

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Adicionar o recurso vinculado à coleção de recursos vinculados da mensagem

message.getLinkedResources().addItem(res);

```
## **Baixar Código em Execução**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Adicionar Imagens Incorporadas à Mensagem de Email](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}