---
title: "Criando e Salvando Arquivos MSG"
url: /pt/python-net/creating-and-saving-msg-files/
weight: 10
type: docs
---

Aspose.Email suporta a criação de arquivos de mensagem do Outlook (MSG). Este artigo explica como:

- Criar mensagens MSG.
- Criar mensagens MSG com anexos.
- Criar uma mensagem MSG com corpo RTF.
- Salvar uma mensagem como rascunho.
- Trabalhar com compressão de corpo.
## **Criando e Salvando Mensagens do Outlook**
A classe MailMessage possui o método Save() que pode salvar arquivos MSG do Outlook no disco ou em um stream. Os trechos de código abaixo criam uma instância da classe MailMessage, definem propriedades como de, para, assunto e corpo. O método Save() aceita o nome do arquivo como um argumento. Além disso, as mensagens do Outlook podem ser criadas com um corpo RTF comprimido usando o MapiConversionOptions. Para configurar, crie um novo aplicativo Windows e adicione uma referência à dll Aspose.Email ao projeto.

1. Crie uma nova instância da classe MailMessage e defina as propriedades From, To, Subject e Body.
1. Chame o método FromMailMessage da classe MailMessage, que aceita um objeto do tipo MailMessage. O método FromMailMessage() converte o MailMessage em um MailMessage (MSG).
1. Chame o método MapiMessage.Save() para salvar o arquivo MSG.

Escreva o seguinte código no evento de clique do controle de botão do aplicativo Windows.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookMSG-CreatingAndSavingOutlookMSG.py" >}}
## **Criando Arquivos MSG Com Anexos**
No exemplo acima, criamos um arquivo MSG simples. Aspose.Email também suporta salvar arquivos de mensagem com anexos. Tudo que você precisa fazer é adicionar os anexos à instância MailMessage. Adicione anexos chamando o método Add() na coleção MailMessage.Attachments. Adicione uma listbox ao formulário criado acima e adicione dois botões, um para adicionar e outro para remover anexos. A aplicação que adiciona anexos funciona assim:

1. Quando o botão **Add Attachment** é clicado, um **Diálogo de Abertura de Arquivo** é exibido para ajudar os usuários a navegar e selecionar o anexo.
1. Quando um arquivo é selecionado, o caminho completo é adicionado a uma lista.
1. Quando o arquivo MSG é criado, os caminhos dos anexos são retirados da lista e adicionados à coleção MailMessage.Attachments.

Escreva o seguinte código no evento de clique do botão **Add Attachment**.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingMSGAttachments-AddingMSGAttachments.py" >}}

Adicione o código para adicionar os anexos à instância MailMessage. O código final para a função Write Msg é escrito como abaixo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingMSGAttachments-AddingMSGAttachments.py" >}}

## **Criando Arquivos MSG Com Corpo RTF**
Você também pode criar arquivos de Mensagem do Outlook (MSG) com corpos de texto rico (RTF) com Aspose.Email. O corpo RTF suporta formatação de texto. Crie um definindo a propriedade MailMessage.HtmlBody. Ao converter uma instância MailMessage em uma instância MailMessage, o corpo HTML é convertido em RTF. Dessa forma, a formatação do corpo do e-mail é preservada.

O seguinte exemplo cria um arquivo MSG com um corpo RTF. Há um cabeçalho, formatação em negrito e sublinhado aplicadas no corpo HTML. Essa formatação é mantida quando o HTML é convertido em RTF.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingMSGFilesWithRtfBody-CreatingMSGFilesWithRtfBody.py" >}}
## **Salvando Mensagem em Status de Rascunho**
Os e-mails são salvos como rascunhos quando alguém começa a editá-los, mas quer retornar a eles para completá-los mais tarde. Aspose.Email suporta salvar mensagens de e-mail em status de rascunho definindo uma flag de mensagem. Abaixo está o código de exemplo para salvar uma mensagem de e-mail do Outlook (MSG) como um rascunho.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SavingMessageInDraftStatus-SavingMessageInDraftStatus.py" >}}
## **Implicações da Compressão de Corpo**
O método de compressão de corpo RTF pode ser usado para gerar um arquivo MSG de menor tamanho. No entanto, isso resulta em uma velocidade mais lenta. Para criar mensagens com velocidade melhorada, defina a flag como falsa. Essa flag, por sua vez, afeta os PSTs criados: arquivos MSG menores resultam em PSTs menores, e grandes arquivos MSG resultam em criação de PST mais lenta.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetBodyCompression-SetBodyCompression.py" >}}