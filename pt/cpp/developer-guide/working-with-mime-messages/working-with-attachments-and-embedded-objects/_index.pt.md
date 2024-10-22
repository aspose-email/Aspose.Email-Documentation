---
title: "Trabalhando com Anexos e Objetos Embutidos usando a Biblioteca C++ Email Parser"
description: "Você pode adicionar e remover anexos de e-mail, exibir o nome do arquivo anexo e trabalhar com objetos embutidos usando a API da Biblioteca C++ Email Parser."
url: /pt/cpp/trabalhando-com-anexos-e-objetos-embutidos/
weight: 50
type: docs
linktitle: "Trabalhando com Anexos e Objetos Embutidos"
---

## **Gerenciando Anexos de E-mail**
Um anexo de e-mail é um arquivo de computador que é enviado juntamente com uma mensagem de e-mail. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. A classe Attachment é usada com a classe MailMessage. Todas as mensagens incluem um corpo. Além do corpo, você pode querer enviar arquivos adicionais. Estes são enviados como anexos e são representados como instâncias da classe Attachment. Você pode enviar qualquer número de anexos, mas o tamanho do anexo é limitado pelo servidor de e-mail. O Gmail, por exemplo, não suporta tamanhos de arquivo superiores a 10MB.
{{% alert %}}
**Experimente!**

Adicione ou remova anexos de e-mail com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}
### **Adicionando Anexo**
Para anexar um anexo a um e-mail, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Crie uma instância da classe Attachment.
1. Carregue o anexo na instância Attachment.
1. Adicione a instância Attachment na instância da classe MailMessage.

O seguinte trecho de código mostra como adicionar um anexo a um e-mail.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-AddEmailAttachments-AddEmailAttachments.cpp" >}}

Acima, descrevemos como adicionar anexos à sua mensagem de e-mail com Aspose.Email. O que se segue mostra como remover anexos e exibir informações sobre eles na tela.

### **Removendo um Anexo**
Para remover um anexo, siga os passos abaixo:

- Crie uma instância da classe Attachment.
- Carregue o anexo na instância da classe Attachment.
- Adicione o anexo à instância da classe MailMessage.
- Remova os anexos da instância da classe Attachment usando a instância da classe MailMessage.

O seguinte trecho de código mostra como remover um anexo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-RemoveAttachments-RemoveAttachments.cpp" >}}

### **Exibindo o Nome do Arquivo Anexo**
Para exibir o nome do arquivo anexo, siga estas etapas:

1. Percorra os anexos na mensagem de e-mail e
   1. Salve cada anexo.
   1. Exiba o nome de cada anexo na tela.

O seguinte trecho de código mostra como exibir o nome de um arquivo anexo na tela.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-DisplayAttachmentFileName-DisplayAttachmentFileName.cpp" >}}

### **Extraindo Anexos de E-mail**
Este tópico explica como extrair um anexo de um arquivo de e-mail. Um anexo de e-mail é um arquivo de computador que é enviado juntamente com uma mensagem de e-mail. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. Todas as mensagens de e-mail incluem um corpo. Assim como o corpo, você pode querer enviar arquivos adicionais. Estes são enviados como anexos e são representados como instâncias da classe Attachment. A classe Attachment é usada com a classe MailMessage para trabalhar com anexos. Para extrair anexos de uma mensagem de e-mail, siga estas etapas:

- Crie uma instância da classe MailMessage.
- Carregue um arquivo de e-mail na instância MailMessage.
- Crie uma instância da classe Attachment e use-a em um loop para extrair todos os anexos.
- Salve o anexo e exiba-o na tela.
- Especifique o endereço do remetente e do destinatário na instância MailMessage.
- Os trechos de código extraem anexos de um e-mail.

|**Anexos extraídos no e-mail**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
O seguinte trecho de código mostra como extrair anexos de e-mail.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cpp" >}}
#### **Recuperando o Content-Description do Anexo**
A API Aspose.Email fornece a capacidade de ler o Content-Description do anexo a partir do cabeçalho do anexo. O seguinte trecho de código mostra como recuperar a descrição do conteúdo do anexo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-RetrieveContentDescriptionFromAttachment-RetrieveContentDescriptionFromAttachment.cpp" >}}
## **Trabalhando com Objetos Embutidos**
Um objeto embutido é um objeto que foi criado com um aplicativo e encerrado dentro de um documento ou arquivo criado por outro aplicativo. Por exemplo, uma planilha do Microsoft Excel pode ser embutida em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser embutido em uma apresentação do Microsoft PowerPoint. Quando um arquivo é embutido, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento embutido pode ser aberto no aplicativo original e modificado.
### **Embutindo Objetos em um E-mail**
A classe LinkedResources é usada com a classe MailMessage para embutir objetos em suas mensagens de e-mail. Para adicionar um objeto embutido, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Especifique os valores do remetente, destinatário e assunto na instância MailMessage.
1. Crie uma instância da classe AlternateView.
1. Crie uma instância da classe LinkedResources.
1. Carregue um objeto embutido na instância LinkedResources.
1. Adicione o objeto embutido carregado na instância da classe MailMessage.
1. Adicione a instância de AlternateViews à instância da classe MailMessage.

Os trechos de código abaixo produzem uma mensagem de e-mail com corpos em texto simples e HTML e uma imagem embutida no HTML.

|**Imagem embutida no e-mail**|
| :- |
|![todo:image_alt_text](/plugins/servlet/confluence/placeholder/unknown-attachment)|
Você pode enviar qualquer número de objetos embutidos. O tamanho do anexo é limitado pelo servidor de e-mail. O Gmail, por exemplo, não suporta tamanhos de arquivo superiores a 10MB. Os trechos de código abaixo mostram como embutir objetos em um e-mail.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-EmbeddedObjects-EmbeddedObjects.cpp" >}}
### **Extraindo Objetos Embutidos**
Este tópico explica como extrair objetos embutidos de um arquivo de e-mail. Um objeto embutido é um objeto que foi criado com um aplicativo e encerrado dentro de um documento ou arquivo criado por outro aplicativo. Por exemplo, uma planilha do Microsoft Excel pode ser embutida em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser embutido em uma apresentação do Microsoft PowerPoint. Quando um arquivo é embutido, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento embutido pode ser aberto no aplicativo original e modificado. Para extrair um objeto embutido de uma mensagem de e-mail, siga estas etapas:

1. Crie uma instância da classe MailMessage.
1. Carregue um arquivo de e-mail na instância MailMessage.
1. Crie um loop e crie uma instância da classe Attachment nele.
1. Salve o anexo e exiba-o na tela.
1. Especifique o endereço do remetente e do destinatário na instância MailMessage.
1. O trecho de código abaixo extrai objetos embutidos de um e-mail.

|**Objetos embutidos extraídos no e-mail**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
O seguinte trecho de código mostra como extrair objetos embutidos.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cpp" >}}