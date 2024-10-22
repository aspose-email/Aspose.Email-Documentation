---
title: "Mostrar e Ocultar Cabeçalhos de Impressão Extras usando MHTFormatOptions"
url: /pt/java/show-and-hide-extra-print-headers-using-mhtformatoptions/
weight: 40
type: docs
---

## **Aspose.Email - Mostrar e Ocultar Cabeçalhos de Impressão Extras usando MHTFormatOptions**
Cabeçalhos de impressão extras podem ser mostrados ou ocultados com MhtFormatOptions e MailMessageSaveOptions. MhtFormatOptions é um enumerador que contém dois membros - WriteCompleteEmailAddressToMht e HideExtraPrintHeader. MhtFormatOptions é usado com MhtMessageFormatter, pois o método público MhtMessageFormatter.Format com o argumento writeCompleteEmailAddress está obsoleto agora.

**Java**

```java
 String dataPath = "src/asposefeatures/programmingemail/showhideextraprintheaders/data/";

String pageHeader = "<div><div class='pageHeader'>&quot;Panditharatne, Mithra&quot; &lt;mithra.panditharatne@cibc.com&gt;<hr/></div>";

MailMessage message = MailMessage.load(dataPath + "message.eml");

MhtMessageFormatter mailFormatter = new MhtMessageFormatter();

int options =  MhtFormatOptions.HideExtraPrintHeader | MhtFormatOptions.WriteCompleteEmailAddressToMht;

mailFormatter.format(message, options);

if(!message.getHtmlBody().contains(pageHeader))

	System.out.println("True");

else

	System.out.println("False");
```
## **Baixar Código em Execução**
Baixe **Mostrar e Ocultar Cabeçalhos de Impressão Extras usando MHTFormatOptions** de qualquer um dos sites de codificação social mencionados abaixo:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)