---
title: "Чтение сообщений электронной почты из библиотеки документов Microsoft SharePoint"
url: /ru/net/reading-email-messages-from-microsoft-sharepoint-document-library/
weight: 110
type: docs
---


В этой статье показано, как читать сообщения электронной почты из библиотеки документов Microsoft SharePoint. Для доступа к файлам в библиотеке документов SharePoint необходимо установить SharePoint SDK в системе. SDK предоставляет API, необходимый для входа в систему и доступа к файлам из библиотеки документов.
## **Чтение сообщений электронной почты из SharePoint**
В приведенных ниже примерах программирования предполагается, что файл сообщений Microsoft Outlook (.msg) уже хранится в папке SharedDocument библиотеки документов SharePoint. SharePoint SDK используется для передачи файла сообщений в поток и последующей передачи этого потока в экземпляр Aspose.Email [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) класс. Класс MailMessage загружает поток и анализирует файл сообщений Outlook. После этого откройте свойства класса MailMessage, например тему, текст, текст, текст HTML и т. д., чтобы использовать информацию в проекте Visual Studio. Сведения об установке и настройке Microsoft SharePoint Server и SDK см. в соответствующих разделах библиотеки MSDN. В следующем фрагменте кода показано, как читать сообщения электронной почты из SharePoint.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-ReadingEmailMessagesFromSharePoint-ReadingEmailMessagesFromSharePoint.cs" >}}
