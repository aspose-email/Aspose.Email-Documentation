---
title: "Чтение email-сообщений из библиотеки документов Microsoft SharePoint"
url: /ru/net/reading-email-messages-from-microsoft-sharepoint-document-library/
weight: 110
type: docs
---

В этой статье показано, как читать email-сообщения из библиотеки документов Microsoft SharePoint. Для доступа к файлам в библиотеке документов SharePoint необходимо установить SDK SharePoint на систему. SDK предоставляет API, необходимый для входа и доступа к файлам из библиотеки документов.
## **Чтение email-сообщений из SharePoint**
Примеры программного кода ниже предполагают, что файл сообщения Microsoft Outlook (.msg) уже сохранен в папке SharedDocument библиотеки документов SharePoint. SDK SharePoint используется для получения файла сообщения в поток, а затем этот поток передается экземпляру класса Aspose.Email's [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage). Класс MailMessage загружает поток и анализирует файл сообщения Outlook. После этого можно получить доступ к свойствам класса MailMessage, таким как тема, текстовое тело, HTML-тело и др., чтобы использовать информацию в проекте Visual Studio. Для получения информации о том, как установить и настроить Microsoft SharePoint Server и SDK, пожалуйста, обратитесь к соответствующим разделам в библиотеке MSDN. Следующий код показывает, как читать email-сообщения из SharePoint.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-ReadingEmailMessagesFromSharePoint-ReadingEmailMessagesFromSharePoint.cs" >}}