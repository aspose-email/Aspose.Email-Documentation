---
title: "Aspose.Email.Функции печати"
url: /ru/net/aspose-email-printing-features/
weight: 150
type: docs
---

## **Функции печати**
The [Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) Пространство имен предоставляет богатый набор функций для печати почтовых сообщений в различных форматах (XPS или TIFF) и настройки макетов страниц. В этой статье они описаны. Существует несколько вариантов распечатки электронного сообщения из Aspose.Email:

1. Печать только текста сообщения.
1. Печать текста и заголовков сообщения.
1. Печать тела HTML.
1. Настройка макета страницы.
1. Автоматическая подгонка TIFF к принтеру.
1. Отрегулируйте целевой DPI для вывода TIFF.
### **Печать текста сообщения**
В следующем фрагменте кода показано, как создать сообщение и распечатать его без заголовков сначала в файл XPS, а затем в файл TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Печать заголовков и текста сообщения**
В следующем фрагменте кода показано, как отображать заголовки и печатать их, а также текст сообщения, изменить [FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) to [MailInfo](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Печать сообщения с текстом HTML**
Сообщения с HTML-текстом также можно распечатать. В следующем фрагменте кода показано, как распечатать сообщение с помощью HTML-текста.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Настройка макета страницы для печати**
[Aspose.Email.Printing.MailPrinter](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter) предоставляет элементы управления для настройки следующих свойств макета страницы:

|**Property**|**Description**|**Значение по умолчанию**|
|: - |: - |: - |
|[FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Показать или скрыть сведения о сообщении. |Нет [1] |
|[MarginTop](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Получите или установите верхнюю маргу.|0.5|
|[MarginLeft](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Получите или установите левое поля.|0.5|
|[MarginBottom](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Получите или установите нижнее марже.|0.5|
|[MarginRight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Получите или установите правильное марже.|0.5|
|[PageUnit](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Получите или установите единицы измерения. |Дюйм [2] |
|[PageHeight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Получите или задайте высоту страницы.|11.69|
|[PageWidth](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Получите или задайте ширину страницы.|8.27|
- Есть два флага: MailInfo и None
- Единицами измерения страницы могут быть дюймы, пиксели, точки, сантиметры или миллиметры.

В приведенном ниже фрагменте кода используются произвольные настройки для иллюстрации использования этих свойств. Он создает страницу высотой 20 см и шириной 8 см с полями 2 см.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Автоматическая подгонка TIFF**
[Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) обеспечивает [MessageFormattingFlags.AutoFitWidth](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags) свойство, позволяющее автоматически подгонять TIFF к принтеру. В следующем фрагменте кода показано, как использовать автоматическую подгонку.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Отрегулируйте целевой DPI для выходного TIFF**
В следующем фрагменте кода показано, как использовать DPI для вывода TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}
