---
title: "Primeira Aplicação com Aspose.Email.Outlook"
url: /pt/net/primeira-aplicacao-com-aspose-email-outlook/
weight: 280
type: docs
---


Esta seção demonstra como usar [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). Criamos uma pequena aplicação que carrega um arquivo de mensagem do Outlook (TestMessage.msg) e exibe o assunto, os endereços de remetente e destinatário, e o conteúdo do corpo em um formulário do Windows. Siga estas etapas para criar sua primeira aplicação usando Aspose.Email.Outlook.

1. No Visual Studio, no menu **Arquivo**, selecione **Novo**, depois **Projeto**.
1. Escolha criar uma aplicação para Windows em C# ou VB.NET.
1. Importe a DLL do Aspose.Email na aplicação clicando com o botão direito em **Referência** no Gerenciador de Soluções. Esta será uma aplicação baseada em Windows que mostrará apenas as informações contidas no arquivo de mensagem.
1. Crie uma instância da classe [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage) fornecendo o caminho do arquivo de mensagem.
1. Use as propriedades públicas para exibir o assunto, de, para e corpo nos controles do Windows.

A implementação das etapas acima é demonstrada abaixo no seguinte trecho de código. Use o seguinte código atrás do botão **Carregar Arquivo Msg** ou no evento OnLoad dos formulários.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}