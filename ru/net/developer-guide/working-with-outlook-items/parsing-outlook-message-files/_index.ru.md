---
title: "Парсинг файлов сообщений Outlook"
url: /ru/net/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Используя Aspose.Email для .NET, разработчики могут не только загружать, но и парсить содержимое из файлов сообщений Outlook.

- Для загрузки файлов MSG с диска используйте статический метод [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
- Для парсинга содержимого файла MSG класс [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) предоставляет ряд методов и свойств.

В этой теме показано, как загрузить и разобрать файл MSG, чтобы отобразить его содержимое.

{{% /alert %}} 

Aspose.Email для .NET предоставляет класс [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), который используется для открытия и парсинга файла MSG. Поскольку в файле MSG может быть много получателей, класс [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) предоставляет свойство [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/), которое возвращает [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/), представляющую собой коллекцию объектов [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/). Объект [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) дополнительно предоставляет методы для работы с атрибутами получателя.

Следующая последовательность шагов служит этой цели:

1. Создайте экземпляр класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с использованием статического метода [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/).
1. Отобразите имя отправителя, тему и тело из файла MSG, используя свойства [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) и [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/).
1. Используйте свойство [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) для получения ссылки на коллекцию объектов [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/), связанных с файлом MSG.
1. Проходите по коллекции [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/), чтобы отобразить содержимое для каждого объекта [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) с помощью его публичных методов.

```cs
// Путь к каталогу ресурсов.
string dataDir = RunExamples.GetDataDir_Email();

//Создайте экземпляр файла MSG для загрузки файла MSG с диска
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Отобразите имя отправителя
Console.WriteLine("Имя отправителя : " + outlookMessageFile.SenderName);
//Отобразите тему
Console.WriteLine("Тема : " + outlookMessageFile.Subject);
//Отобразите тело
Console.WriteLine("Тело : " + outlookMessageFile.Body);
//Отобразите информацию о получателе
Console.WriteLine("Получатели : \n");

//Проходите по коллекции получателей, связанной с объектом MapiMessage
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Отобразите адрес электронной почты получателя
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Отобразите имя получателя
	Console.WriteLine("Имя : " + rcp.DisplayName);
	//Отобразите тип получателя
	Console.WriteLine("Тип получателя : " + rcp.RecipientType);
}
```

{{% alert %}}
**Попробуйте это!**

Парсите файлы электронной почты онлайн с бесплатным [**Aspose.Email Parser App**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}