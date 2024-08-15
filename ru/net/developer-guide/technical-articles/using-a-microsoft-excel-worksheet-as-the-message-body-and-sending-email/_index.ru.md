---
title: "Использование рабочего листа Microsoft Excel в качестве текста сообщения и отправка электронной почты"
url: /ru/net/using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email/
weight: 160
type: docs
---


В этой статье в качестве текста письма используется рабочая книга Microsoft Excel, и она отправляется получателям. Aspose.Email for .NET занимается сетевыми протоколами и функциями Microsoft Outlook и не может работать с рабочими книгами Microsoft Excel. Чтобы решить эту проблему, в примерах этой статьи используется Aspose.Cells for .NET для загрузки рабочей книги Excel и преобразования ее в поток HTML. Затем Aspose.Email для .NET использует поток HTML в теле письма. В примере программирования показано, как отправить рабочий лист Excel в виде текста письма с помощью Aspose.Cells для .NET и Aspose.Email для .NET

1. Загрузка рабочей книги Microsoft Excel с использованием класса рабочей книги Aspose.Cells
1. Сохраните загруженную рабочую книгу в MemoryStream в формате HTML
1. Получите HTML-код из потока в виде строки
1. Определите новый объект MailMessage и настройте его HTMLBody на HTML-содержимое, описанное в шаге 3
1. Отправьте электронное письмо, используя Aspose.Email для класса SMTPClient от .NET

Исходную рабочую книгу Excel можно увидеть следующим образом:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_1.png)



Когда сообщение было отправлено и получено в Microsoft Outlook, оно выглядит следующим образом:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_2.png)



В следующем фрагменте кода показано, как отправить рабочий лист MS Excel в качестве текста сообщения и отправить электронное письмо.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendExcelWorksheetAsMessageBody-SendExcelWorksheetAsMessageBody.cs" >}}
