---
title: "Возможности печати Aspose.Email"
url: /ru/net/aspose-email-printing-features/
weight: 150
type: docs
---

## **Возможности печати**
Пространство имен [Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) предоставляет богатый набор функций для печати сообщений электронной почты в различные форматы (XPS или TIFF) и настройки макетов страниц. В этой статье описаны эти возможности. Существует несколько вариантов, как сообщение электронной почты может быть напечатано из Aspose.Email:

1. Печать только тела сообщения.
1. Печать тела сообщения и заголовков.
1. Печать HTML-тела.
1. Настройка макета страницы.
1. Автоматическая подгонка TIFF под принтер.
1. Настройка целевого разрешения DPI для выходного TIFF.
### **Печать тела сообщения**
Следующий фрагмент кода показывает, как создать сообщение и сначала напечатать его без заголовков в файл XPS, а затем в файл TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Печать заголовков и тела сообщения**
Следующий фрагмент кода показывает, как отобразить заголовки и напечатать их, а также тело сообщения, изменяя [FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) на [MailInfo](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Печать сообщения с HTML-телом**
Сообщения с HTML-телом также могут быть напечатаны. Следующий фрагмент кода показывает, как напечатать сообщение с HTML-телом.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Настройка макета страницы для печати**
[Aspose.Email.Printing.MailPrinter](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter) предоставляет элементы управления для настройки следующих свойств макета страницы:

|**Свойство**|**Описание**|**Значение по умолчанию**|
| :- | :- | :- |
|[FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Показать или скрыть детали сообщения.|Нет [1]|
|[MarginTop](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Получить или установить верхний отступ.|0.5|
|[MarginLeft](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Получить или установить левый отступ.|0.5|
|[MarginBottom](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Получить или установить нижний отступ.|0.5|
|[MarginRight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Получить или установить правый отступ.|0.5|
|[PageUnit](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Получить или установить единицы измерения.|Дюйм [2]|
|[PageHeight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Получить или установить высоту страницы.|11.69|
|[PageWidth](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Получить или установить ширину страницы.|8.27|
- Существуют два флага: MailInfo и None
- Единицы страниц могут быть одним из: Inch, Pixel, Point, Cm или Millimeter.

Следующий фрагмент кода использует произвольные настройки, чтобы проиллюстрировать, как используются эти свойства. Он настраивает страницу высотой 20 см и шириной 8 см с отступами 2 см.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Автоматическая подгонка TIFF**
[Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) предоставляет свойство [MessageFormattingFlags.AutoFitWidth](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags), которое позволяет автоматически подгонять TIFF под принтер. Следующий фрагмент кода показывает, как использовать автоматическую подгонку.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Настройка целевого DPI для выходного TIFF**
Следующий фрагмент кода показывает, как использовать DPI для выходного TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}