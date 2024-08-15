---
title: "Разбор файлов сообщений Outlook"
url: /ru/net/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}}

Используя Aspose.Email для .NET, разработчики могут не только загружать, но и анализировать содержимое файлов сообщений Outlook.

- Чтобы загрузить файлы MSG с диска, используйте статический [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) метод [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class.
- Чтобы проанализировать содержимое файла MSG, [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) раскрывает ряд методов и свойств.

В этом разделе показано, как загрузить и проанализировать файл MSG для отображения его содержимого.

{{% /alert %}}

Aspose.Email для .NET предоставляет [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс, который используется для открытия и анализа файла MSG. Поскольку в файле MSG может быть много получателей, [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс раскрывает [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) свойство, возвращающее [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) который представляет собой коллекцию [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) объекты. [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) объект дополнительно предоставляет методы работы с атрибутами получателя.

Для этого используется следующая последовательность шагов:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс, использующий [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) статический метод.
1. Отобразите имя, тему и текст отправителя из файла MSG, используя [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) and [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/) properties.
1. Используйте [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) недвижимость, в которой можно получить ссылку на коллекцию [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) объекты, связанные с файлом MSG.
1. Пройдите через [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) коллекция для отображения содержимого каждого [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) объект с помощью публичных методов.

```cs
// The path to the resource directory.
string dataDir = RunExamples.GetDataDir_Email();

//Instantiate an MSG file to load an MSG file from disk
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Display sender's name
Console.WriteLine("Sender Name : " + outlookMessageFile.SenderName);
//Display Subject
Console.WriteLine("Subject : " + outlookMessageFile.Subject);
//Display Body
Console.WriteLine("Body : " + outlookMessageFile.Body);
//Display Recipient's info
Console.WriteLine("Recipients : \n");

//Пройдите через recipients collection associated with the MapiMessage object
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Display recipient email address
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Display recipient name
	Console.WriteLine("Name : " + rcp.DisplayName);
	//Display recipient type
	Console.WriteLine("Recipient Type : " + rcp.RecipientType);
}
```

{{% alert %}}
**Попробуйте!**

Анализируйте файлы электронной почты онлайн бесплатно [**Приложение для парсера электронной почты Aspose.Email**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}
