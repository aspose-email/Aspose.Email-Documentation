---
title: "Criando e Salvando Arquivos MSG"
url: /pt/net/creating-and-saving-msg-files/
weight: 10
type: docs
---

Aspose.Email suporta a criação de arquivos de mensagem do Outlook (MSG). Este artigo explica como:

- Criar mensagens MSG.
- Criar mensagens MSG com anexos.
- Criar uma mensagem MSG com um corpo RTF.
- Salvar uma mensagem como um rascunho.
- Trabalhar com compressão de corpo.

## **Criando e Salvando Mensagens do Outlook**

A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) possui o método [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) que pode salvar arquivos MSG do Outlook em disco ou em um stream. Os trechos de código abaixo criam uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), configuram propriedades como de, para, assunto e corpo. O método [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) recebe o nome do arquivo como argumento. Além disso, as Mensagens do Outlook podem ser criadas com um [corpo RTF comprimido]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) usando as [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). Para configurar, crie um novo aplicativo do Windows e adicione uma referência à dll do Aspose.Email no projeto.

1. Crie uma nova instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e configure as propriedades From, To, Subject e Body.
2. Chame o método [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que aceita o objeto do tipo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O método [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) converte o [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) em um [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Chame o método [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) para salvar o arquivo MSG.

Escreva o seguinte código no evento de clique do controle de botão do aplicativo do Windows.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Criando Arquivos MSG Com Anexos**

[No exemplo acima](https://docs.aspose.com/email/pt/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), criamos um arquivo MSG simples. Aspose.Email também suporta o salvamento de arquivos de mensagem com anexos. Tudo o que você precisa fazer é adicionar os anexos à instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Adicione anexos chamando o método *Add()* na coleção [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/). Adicione uma caixa de listagem ao formulário criado acima e adicione dois botões, um para adicionar e outro para remover anexos. O aplicativo que adiciona anexos funciona assim:

1. Quando o botão **Adicionar Anexo** é clicado, um **Diálogo de Abertura de Arquivo** é exibido para ajudar os usuários a navegar e selecionar o anexo.
2. Quando um arquivo é selecionado, o caminho completo é adicionado a uma lista.
3. Quando o arquivo MSG é criado, os caminhos dos anexos são extraídos da lista e adicionados à coleção [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/).

Escreva o seguinte código no evento de clique do botão **Adicionar Anexo**.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

Quando o botão **Remover Anexo** é clicado, remova os itens selecionados da caixa de listagem. Escreva o seguinte código no evento de clique do botão Remover Anexo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Adicione o código para adicionar os anexos à instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). O código final para a função Write Msg é escrito como abaixo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Criando Arquivos MSG Com Corpo RTF**

Você também pode criar arquivos de Mensagem do Outlook (MSG) com corpos de texto rico (RTF) com o Aspose.Email. O corpo RTF suporta formatação de texto. Crie um configurando a propriedade [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/). Quando você converte uma instância [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) em uma instância [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), o corpo HTML é convertido em RTF. Dessa forma, a formatação do corpo do e-mail é preservada.

O exemplo a seguir cria um arquivo MSG com um corpo RTF. Há um título, formatação em negrito e sublinhado aplicados no corpo HTML. Essa formatação é mantida quando o HTML é convertido em RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

## **Salvando Mensagem em Status de Rascunho**

Emails são salvos como rascunhos quando alguém começou a editá-los, mas deseja voltar a eles para completá-los mais tarde. Aspose.Email suporta o salvamento de mensagens de e-mail em status de rascunho definindo uma flag de mensagem. Abaixo está o código de exemplo para salvar uma mensagem de e-mail do Outlook (MSG) como um rascunho.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}

## **Compressão RTF ao definir o corpo da mensagem MAPI**

> **_NOTA:_** O processo de compressão pode desacelerar o desempenho ao criar mensagens. Ao entender esse fato e configurar a flag de compressão com base em requisitos específicos e compromissos entre o tamanho do arquivo e o desempenho, os desenvolvedores podem gerenciar efetivamente a criação de arquivos MSG e PST ao lidar com mensagens de e-mail.

Nesta seção, você aprenderá como usar a compressão RTF ao definir o corpo da mensagem MAPI. A compressão RTF é destinada a reduzir o tamanho de uma mensagem, assim como os arquivos PST (Tabela de Armazenamento Pessoal) resultantes que o Microsoft Outlook usa para armazenar mensagens de e-mail e outros dados. Ao usar a compressão RTF ao configurar o corpo da mensagem, os desenvolvedores podem reduzir a quantidade de memória necessária para armazenar mensagens de e-mail ou otimizar a largura de banda da rede ao transmitir mensagens.

Para esse propósito, foram projetados dois métodos sobrecarregados:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(string content, BodyContentType contentType, bool compression): Este método permite que você defina o conteúdo do corpo da mensagem usando o conteúdo de string especificado e especificando o tipo de conteúdo do corpo (por exemplo, texto simples, HTML, etc.). O parâmetro de compressão opcional é um valor que especifica se o conteúdo deve ser comprimido usando compressão RTF. Se o parâmetro de compressão for verdadeiro, o conteúdo será comprimido, resultando em um tamanho de mensagem menor.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(string content, bool compression): Este método define especificamente o conteúdo do corpo da mensagem no formato RTF. O parâmetro de conteúdo é uma string representando o conteúdo RTF que será definido como o corpo da mensagem. Assim como no método anterior, o parâmetro de compressão determina se a compressão RTF deve ser aplicada ao conteúdo. Se a compressão for verdadeira, o conteúdo RTF será comprimido para reduzir o tamanho.

O seguinte exemplo de código mostra como definir um corpo html e mantê-lo comprimido:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// definir o corpo html e mantê-lo comprimido
// isso reduzirá o tamanho da mensagem
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

Há também uma propriedade [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/). Quando esta propriedade está habilitada, a compressão do corpo RTF é aplicada durante a conversão de MailMessage para MapiMessage, resultando em um menor tamanho de arquivo MSG. Isso é mostrado no exemplo de código abaixo:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```