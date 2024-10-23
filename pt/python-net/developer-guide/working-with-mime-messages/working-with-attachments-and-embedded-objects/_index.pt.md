---
title: "Trabalhando com Anexos e Objetos Incorporados"
url: /pt/python-net/trabalhando-com-anexos-e-objetos-incorporados/
weight: 50
type: docs
---

## **Gerenciando Anexos de Email**
Um anexo de email é um arquivo de computador que é enviado junto com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. A classe Attachment é usada com a classe MailMessage. Todas as mensagens incluem um corpo. Além do corpo, você pode querer enviar arquivos adicionais. Estes são enviados como anexos e são representados como instâncias da classe Attachment. Você pode enviar qualquer número de anexos, mas o tamanho do anexo é limitado pelo servidor de email. O Gmail, por exemplo, não suporta tamanhos de arquivos superiores a 10MB.
{{% alert %}}
**Experimente!**

Adicione ou remova anexos de email online com o gratuito [**Aspose.Email Editor App**](https://products.aspose.app/email/pt/editor).
{{% /alert %}}
### **Adicionando Anexo**
Para anexar um anexo a um email, siga estes passos:

1. Crie uma instância da classe MailMessage.
1. Crie uma instância da classe Attachment.
1. Carregue o anexo na instância de Attachment.
1. Adicione a instância de Attachment na instância da classe MailMessage.

O seguinte trecho de código mostra como adicionar um anexo a um email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AddEmailAttachments-AddEmailAttachments.py" >}}

Acima, descrevemos como adicionar anexos à sua mensagem de email com o Aspose.Email. O que segue mostra como remover anexos e exibir informações sobre eles na tela.
### **Removendo um Anexo**
Para remover um anexo, siga os passos abaixo:

- Crie uma instância da classe Attachment.
- Carregue o anexo na instância da classe Attachment.
- Adicione o anexo à instância da classe MailMessage.
- Remova os anexos da instância da classe Attachment usando a instância da classe MailMessage.

O seguinte trecho de código mostra como remover um anexo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemovingAttachmentFromMailMessage-RemovingAttachmentFromMailMessage.py" >}}
### **Exibindo o Nome do Arquivo do Anexo**
Para exibir o nome do arquivo do anexo, siga estes passos:

1. Percorra os anexos na mensagem de email e
   1. Salve cada anexo.
   1. Exiba o nome de cada anexo na tela.

O seguinte trecho de código mostra como exibir o nome do arquivo de um anexo na tela.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayAttachmentFileName-DisplayAttachmentFileName.py" >}}
### **Extraindo Anexos de Email**
Este tópico explica como extrair um anexo de um arquivo de email. Um anexo de email é um arquivo de computador que é enviado junto com uma mensagem de email. O arquivo pode ser enviado como uma mensagem separada, bem como parte da mensagem à qual está anexado. Todas as mensagens de email incluem um corpo. Assim como o corpo, você pode querer enviar arquivos adicionais. Esses são enviados como anexos e são representados como instâncias da classe Attachment. A classe Attachment é usada com a classe MailMessage para trabalhar com anexos. Para extrair anexos de uma mensagem de email, siga estes passos:

- Crie uma instância da classe MailMessage.
- Carregue um arquivo de email na instância da MailMessage.
- Crie uma instância da classe Attachment e use-a em um loop para extrair todos os anexos.
- Salve o anexo e exiba-o na tela.
- Especifique o endereço do remetente e do destinatário na instância da MailMessage.
- Agora você pode enviar email usando a classe SmtpClient.

Os trechos de código extraem anexos de um email.

|**Anexos extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
O seguinte trecho de código mostra como extrair anexos de email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}
#### **Recuperando Content-Description do Anexo**
A API Aspose.Email fornece a capacidade de ler a Content-Description do anexo do cabeçalho do anexo. O seguinte trecho de código mostra como recuperar a descrição do conteúdo de um anexo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RetrievContentDescriptionFromAttachment-RetrievContentDescriptionFromAttachment.py" >}}
#### **Determinando se o Anexo é uma Mensagem Incorporada**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DetermineAttachmendEmbeddedMessage-DetermineAttachmendEmbeddedMessage.py" >}}
## **Trabalhando com Objetos Incorporados**
Um objeto incorporado é um objeto que foi criado com um aplicativo e inserido dentro de um documento ou arquivo criado por outro aplicativo. Por exemplo, uma planilha do Microsoft Excel pode ser incorporada em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser incorporado em uma apresentação do Microsoft PowerPoint. Quando um arquivo é incorporado, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento incorporado pode ser aberto no aplicativo original e modificado.
### **Incorporando Objetos em um Email**
Removendo Objetos Incorporados de um Email

LinkedResourceCollection, acessada através da propriedade MailMessage.LinkedResources, fornece métodos para remover completamente objetos incorporados adicionados a uma mensagem de email. Use a versão sobrecarregada do método LinkedResourceCollection.RemoveAt para remover todas as evidências de um objeto incorporado de uma mensagem de email.

O código de exemplo abaixo mostra como remover objetos incorporados de uma mensagem de email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemoveLRTracesFromMessageBody-RemoveLRTracesFromMessageBody.py" >}}
### **Extraindo Objetos Incorporados**
Este tópico explica como extrair objetos incorporados de um arquivo de email. Um objeto incorporado é um objeto que foi criado com um aplicativo e inserido dentro de um documento ou arquivo criado por outro aplicativo. Por exemplo, uma planilha do Microsoft Excel pode ser incorporada em um relatório do Microsoft Word, ou um arquivo de vídeo pode ser incorporado em uma apresentação do Microsoft PowerPoint. Quando um arquivo é incorporado, em vez de inserido ou colado em outro documento, ele mantém seu formato original. O documento incorporado pode ser aberto no aplicativo original e modificado. Para extrair um objeto incorporado de uma mensagem de email, siga estes passos:

1. Crie uma instância da classe MailMessage.
1. Carregue um arquivo de email na instância da MailMessage.
1. Crie um loop e crie uma instância da classe Attachment nele.
1. Salve o anexo e exiba-o na tela.
1. Especifique o endereço do remetente e do destinatário na instância da MailMessage.
1. Envie email usando a classe SmtpClient.

O trecho de código abaixo extrai objetos incorporados de um email.

|**Objetos incorporados extraídos no email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
O seguinte trecho de código mostra como extrair objetos incorporados.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}