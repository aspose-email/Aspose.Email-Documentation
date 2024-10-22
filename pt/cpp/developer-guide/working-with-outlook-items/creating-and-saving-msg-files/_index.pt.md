---
title: "Criando e Salvando arquivos MSG do Outlook usando a C++ Email API"
description: "A API de Parser de Email em C++ suporta a criação de arquivos de mensagem MSG do Outlook com anexos, corpo RTF e salvar a mensagem como rascunho."
url: /pt/cpp/creating-and-saving-msg-files/
weight: 10
type: docs
linktitle: "Criando e Salvando arquivos MSG"
---

## **Criando e Salvando arquivos MSG**
Aspose.Email suporta a criação de arquivos de mensagem do Outlook (MSG). Este artigo explica como:

- Criar mensagens MSG.
- Criar mensagens MSG com anexos.
- Criar uma mensagem MSG com corpo RTF.
- Salvar uma mensagem como rascunho.
- Trabalhar com compressão de corpo.

### **Criando e Salvando Mensagens do Outlook**
A classe MailMessage possui o método Save() que pode salvar arquivos MSG do Outlook no disco ou em um stream. Os trechos de código abaixo criam uma instância da classe MailMessage, configuram propriedades como de, para, assunto e corpo. O método Save() aceita o nome do arquivo como argumento. Além disso, as Mensagens do Outlook podem ser criadas com um corpo RTF comprimido usando as MapiConversionOptions. Para configurar, crie uma nova aplicação Windows e adicione uma referência à dll Aspose.Email no projeto.

1. Crie uma nova instância da classe MailMessage e configure as propriedades From, To, Subject e Body.
1. Chame o método FromMailMessage da classe MailMessage que aceita um objeto do tipo MailMessage. O método FromMailMessage() converte o MailMessage em um MailMessage (MSG).
1. Chame o método MapiMessage.Save() para salvar o arquivo MSG.

Escreva o seguinte código no evento de clique do controle de botão da aplicação Windows.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cpp" >}}

### **Criando arquivos MSG com corpo RTF**
Você também pode criar arquivos de Mensagem do Outlook (MSG) com corpos de texto rico (RTF) com Aspose.Email. O corpo RTF suporta formatação de texto. Crie um definindo a propriedade MailMessage.HtmlBody. Quando você converte uma instância de MailMessage em uma instância de MailMessage, o corpo HTML é convertido em RTF. Assim, a formatação do corpo do email é preservada.

O exemplo a seguir cria um arquivo MSG com um corpo RTF. Há um cabeçalho, formatação em negrito e sublinhado aplicada no corpo HTML. Essa formatação é mantida quando o HTML é convertido em RTF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cpp" >}}

### **Salvando Mensagem em Status de Rascunho**
Emails são salvos como rascunhos quando alguém começou a editá-los, mas deseja retorná-los para completá-los mais tarde. Aspose.Email suporta salvar mensagem de email em status de rascunho definindo uma flag de mensagem. Abaixo está o código de exemplo para salvar uma mensagem de email do Outlook (MSG) como um rascunho.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cpp" >}}

### **Implicações da Compressão do Corpo**
O método de compressão de corpo RTF pode ser usado para gerar um MSG de tamanho menor. No entanto, isso resulta em velocidade mais lenta. Para criar mensagens com velocidade melhorada, defina a flag como falsa. Essa flag, por sua vez, tem efeito sobre os PSTs criados: arquivos MSG menores resultam em PST menores, e arquivos MSG grandes resultam em criação de PST mais lenta.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetBodyCompression-SetBodyCompression.cpp" >}}