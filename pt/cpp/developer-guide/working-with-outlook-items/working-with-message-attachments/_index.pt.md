---
title: "Trabalhando com Anexos de Mensagens do Outlook usando a API de Análise de E-mail em C++"
description: "Você pode gerenciar anexos de mensagens do Outlook com a Biblioteca de Análise de E-mail em C++, salvá-los e excluí-los, e incorporar mensagens como um anexo."
url: /pt/cpp/trabalhando-com-anexos-de-mensagens/
weight: 70
type: docs
linktitle: "Trabalhando com Anexos de Mensagens"
---

## **Gerenciando Anexos com Aspose Outlook**
Criar e Salvar Arquivos de Mensagem do Outlook (MSG) explicou como criar e salvar mensagens, e como criar arquivos MSG com anexos. Este artigo explica como gerenciar anexos do Microsoft Outlook com Aspose.Email. Anexos de um arquivo de mensagem são acessados e salvos no disco usando a propriedade Attachments da classe MapiMessage. A propriedade Attachments é uma coleção do tipo MapiAttachmentCollection.

### **Salvar Anexos de Arquivo de Mensagem do Outlook (MSG)**
Para salvar anexos de um arquivo MSG:

1. Percorra a coleção MapiAttachmentCollection e obtenha os anexos individuais.
1. Para salvar os anexos, chame o método Save() da classe MapiAttachment.

O seguinte trecho de código mostra como salvar anexos no disco local.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Removendo Anexos**
A biblioteca Aspose Outlook fornece a funcionalidade para remover anexos de arquivos de Mensagem do Microsoft Outlook (.msg):

- Chame o método RemoveAttachments(). Ele recebe o caminho do arquivo de mensagem como um parâmetro. É implementado como um método estático público, portanto, você não precisa instanciar o objeto.

O seguinte trecho de código mostra como remover Anexos usando a Biblioteca de Análise de E-mail em C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

Você também pode chamar o método estático da classe MapiMessage DestroyAttachment(). Ele funciona mais rápido que RemoveAttachment(), porque o método RemoveAttachment() analisa o arquivo de mensagem.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Adicionando Anexos MSG**
Uma mensagem do Outlook pode conter outras mensagens do Microsoft Outlook em anexos, seja como mensagens regulares ou incorporadas. A MapiAttachmentCollection fornece membros sobrecarregados do método Add para criar mensagens do Outlook com ambos os tipos de anexos.

### **Incorporando Mensagem como Anexo**
O seguinte trecho de código mostra como os arquivos MSG do Outlook incorporados em um arquivo MSG contêm um PR_ATTACH_METHOD cujo valor é igual a 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}