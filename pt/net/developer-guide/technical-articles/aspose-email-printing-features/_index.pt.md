---
title: "Recursos de Impressão do Aspose.Email"
url: /pt/net/aspose-email-printing-features/
weight: 150
type: docs
---

## **Recursos de Impressão**
O namespace [Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) fornece um rico conjunto de recursos para imprimir mensagens de e-mail em diferentes formatos (XPS ou TIFF) e configurar layouts de página. Este artigo os descreve. Existem várias opções de como uma mensagem de e-mail pode ser impressa a partir do Aspose.Email:

1. Imprimir apenas o corpo da mensagem.
1. Imprimir o corpo da mensagem e os cabeçalhos.
1. Imprimir um corpo HTML.
1. Configurar o layout da página.
1. Ajustar uma TIFF automaticamente para a impressora.
1. Ajustar a DPI alvo para a saída TIFF.
### **Imprimindo o Corpo da Mensagem**
O seguinte trecho de código mostra como criar uma mensagem e imprimi-la sem cabeçalhos primeiro para um arquivo XPS e depois para um arquivo TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Imprimindo Cabeçalhos e Corpo da Mensagem**
O seguinte trecho de código mostra como exibir os cabeçalhos e imprimi-los, bem como o corpo da mensagem, alterando os [FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) para [MailInfo](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Imprimindo Mensagem com Corpo HTML**
Mensagens com corpo HTML também podem ser impressas. O seguinte trecho de código mostra como imprimir uma mensagem com corpo HTML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Configurando Layout da Página para Impressão**
[Aspose.Email.Printing.MailPrinter](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter) fornece controles para definir as seguintes propriedades do layout da página:

|**Propriedade**|**Descrição**|**Valor Padrão**|
| :- | :- | :- |
|[FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Mostrar ou ocultar detalhes da mensagem.|Nenhum [1]|
|[MarginTop](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Obter ou definir a margem superior.|0.5|
|[MarginLeft](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Obter ou definir a margem esquerda.|0.5|
|[MarginBottom](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Obter ou definir a margem inferior.|0.5|
|[MarginRight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Obter ou definir a margem direita.|0.5|
|[PageUnit](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Obter ou definir as unidades de medida.|Polegada [2]|
|[PageHeight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Obter ou definir a altura da página.|11.69|
|[PageWidth](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Obter ou definir a largura da página.|8.27|
- Existem duas bandeiras: MailInfo e Nenhum
- As unidades da página podem ser uma de Polegada, Pixel, Ponto, Cm ou Milímetro.

O trecho de código a seguir usa configurações arbitrárias para ilustrar como essas propriedades são usadas. Ele configura uma página com 20 cm de altura e 8 cm de largura, com margens de 2 cm.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Ajustar automaticamente uma TIFF**
[Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) fornece a propriedade [MessageFormattingFlags.AutoFitWidth](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags) que permite ajustar automaticamente a TIFF para a impressora. O seguinte trecho de código mostra como usar o ajuste automático.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Ajustar DPI alvo para saída TIFF**
O seguinte trecho de código mostra como usar DPI para saída TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}