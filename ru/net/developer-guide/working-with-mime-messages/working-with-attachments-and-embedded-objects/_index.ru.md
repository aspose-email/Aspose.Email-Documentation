---
title: "Работа с вложениями и встроенными объектами"
url: /ru/net/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Управление вложениями электронной почты**

Вложение электронной почты - это файл, который отправляется вместе с электронным сообщением. Файл может быть отправлен как отдельное сообщение, так и частью сообщения, к которому он прикреплен. Класс [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) используется совместно с классом [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Все сообщения включают текстовое содержание. В дополнение к содержимому вы можете отправлять дополнительные файлы. Они отправляются в виде вложений и представлены как экземпляры класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). Вы можете отправить любое количество вложений, но размер вложения ограничен почтовым сервером. Gmail, например, не поддерживает размеры файлов более 10 МБ.
{{% alert %}}
**Попробуйте это!**

Добавьте или удалите вложения электронной почты онлайн с помощью бесплатного [**Aspose.Email Editor App**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление вложения**

Чтобы добавить вложение к электронной почте, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
3. Загрузите вложение в экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
4. Добавьте экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Следующий фрагмент кода показывает, как добавить вложение к электронному письму.

```csharp
// Создайте экземпляр класса MailMessage
var eml = new MailMessage
{
    From = "sender@from.com",
    To = "receiver@to.com",
    Subject = "Это сообщение",
    Body = "Это содержимое"
};

// Загрузите вложение
var attachment = new Attachment("1.txt");

// Добавьте несколько вложений в экземпляр класса MailMessage и сохраните сообщение на диск
eml.Attachments.Add(attachment);

eml.AddAttachment(new Attachment("1.jpg"));
eml.AddAttachment(new Attachment("1.doc"));
eml.AddAttachment(new Attachment("1.rar"));
eml.AddAttachment(new Attachment("1.pdf"));
eml.Save("AddAttachments.eml");
```

Выше мы описали, как добавить вложения к вашему электронному сообщению с помощью Aspose.Email. Следующий раздел показывает, как удалить вложения и отобразить информацию о них на экране.

### **Добавление ссылочного вложения**

Ссылочное вложение - это тип вложения, который включает ссылку или указание на файл или элемент, а не включает сам файл или элемент в сообщение электронной почты. Когда получатели электронной почты кликают на ссылочное вложение, они смогут получить доступ к связанному файлу, если у них есть соответствующие разрешения. Используя ссылочное вложение, вы можете отправить меньшее сообщение и убедиться, что все имеют доступ к самой актуальной версии файла или элемента.

Ниже приведен пример кода, показывающий, как добавить ссылочное вложение к электронному письму. Код выполняет следующие шаги:

1. Загружает файл электронного сообщения, используя метод [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Создает новый объект ReferenceAttachment под названием refAttach, передавая URL вложения "https://[attach_uri]" в качестве параметра его конструктора.
3. Устанавливает имя вложения на "Document.docx" с помощью свойства [Name](https://reference.aspose.com/email/net/aspose.email/attachment/name/) объекта refAttach.
4. Устанавливает тип провайдера вложения на [AttachmentProviderType.OneDrivePro](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) с помощью свойства [ProviderType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/providertype/) объекта refAttach.
5. Устанавливает тип разрешения вложения на [AttachmentPermissionType.AnyoneCanEdit](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) с помощью свойства [PermissionType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/permissiontype/) объекта refAttach.
6. Добавляет объект refAttach в коллекцию [Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) объекта eml, используя метод [Add()](https://reference.aspose.com/email/net/aspose.email/attachmentcollection/).

```cs
var eml = MailMessage.Load("fileName");

var refAttach = new ReferenceAttachment("https://[attach_uri]")
{
    Name = "Document.docx",
    ProviderType = AttachmentProviderType.OneDrivePro,
    PermissionType = AttachmentPermissionType.AnyoneCanEdit
};

eml.Attachments.Add(refAttach);
```

### **Удаление вложения**

Чтобы удалить вложение, выполните следующие шаги:

- Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Загрузите вложение в экземпляр класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/).
- Добавьте вложение в экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Удалите вложение из экземпляра класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) с использованием экземпляра класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Следующий код показывает, как удалить вложение.

```csharp
// Создайте экземпляр класса MailMessage
var eml = new MailMessage {From = "sender@sender.com", To = "receiver@gmail.com"};

// Загрузите вложение
var attachment = new Attachment("1.txt");
eml.Attachments.Add(attachment);

// Удалите вложение из вашего MailMessage
eml.Attachments.Remove(attachment);
```

### **Отображение имени файла вложения**

Чтобы отобразить имя файла вложения, выполните следующие шаги:

1. Пройдитесь по вложениям в электронном сообщении и сохраните каждое вложение.
2. Отобразите каждое имя вложения на экране.

Следующий фрагмент кода показывает, как отобразить имя файла вложения на экране.

```csharp
var eml = MailMessage.Load("Attachments.eml");

foreach (var attachment in eml.Attachments)
{
    // Отобразите имя файла вложения
    Console.WriteLine(attachment.Name);
}
```

### **Извлечение вложений электронной почты**

Эта тема объясняет, как извлечь вложение из файла электронной почты. Вложение электронной почты - это файл, который отправляется вместе с электронным сообщением. Файл может быть отправлен как отдельное сообщение, так и частью сообщения, к которому он прикреплен. Все электронные сообщения включают возможность отправки дополнительных файлов. Они отправляются в виде вложений и представлены как экземпляры класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/). Класс [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) используется с классом [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для работы с вложениями. Чтобы извлечь вложения из электронного сообщения, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Загрузите файл электронной почты в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) и используйте его в цикле для извлечения всех вложений.
- Сохраните вложение и отобразите его на экране.

|**Извлеченные вложения в электронной почте**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
Следующий фрагмент кода показывает, как извлечь вложения электронной почты.

```csharp
var eml = MailMessage.Load("Message.eml", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.eml");
    Console.WriteLine(attachment.Name);
}
```

#### **Извлечение содержимого описания из вложения**

API Aspose.Email предоставляет возможность считывать содержимое описания вложения из заголовка вложения. Следующий фрагмент кода показывает, как извлечь описание содержимого из вложения.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");
Console.WriteLine(eml.Attachments[0].Headers["Content-Description"]);
```

#### **Определение, является ли вложение встроенным сообщением**

Следующий фрагмент кода демонстрирует, как определить, является ли вложение встроенным сообщением или нет.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");

Console.WriteLine(eml.Attachments[0].IsEmbeddedMessage
    ? "Вложение является встроенным сообщением."
    : "Вложение не является встроенным сообщением.");
```

## **Работа с встроенными изображениями**

### **Добавление встроенного изображения в тело электронной почты**

Класс [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) используется совместно с классом [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для встраивания объектов в ваше электронное сообщение. Чтобы добавить встроенный объект, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Укажите значения от кого, кому и тему в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
3. Создайте экземпляр класса [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview).
4. Создайте экземпляр класса [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/).
5. Загрузите встроенный объект в [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/).
6. Добавьте загруженный встроенный объект в экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
7. Добавьте экземпляр [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) в экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Ниже приведены фрагменты кода, которые создают электронное сообщение с текстовым и HTML содержанием и изображением, встроенным в HTML.

|**Изображение, встроенное в электронное письмо**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Вы можете отправить любое количество встроенных объектов. Размер вложения ограничен почтовым сервером. Gmail, например, не поддерживает размеры файлов более 10 МБ. Ниже приведены фрагменты кода, демонстрирующие, как встроить объекты в электронную почту.

```csharp
var eml = new MailMessage
{
    From = "AndrewIrwin@from.com",
    To = "SusanMarc@to.com",
    Subject = "Это электронное письмо"
};

// Создайте часть с простым текстом. Она будет доступна тем клиентам, которые не поддерживают HTML.
var plainView =
    AlternateView.CreateAlternateViewFromString("Это мое содержание в простом тексте", null, "text/plain");

// Создайте HTML часть. Чтобы встроить изображения, нужно использовать префикс 'cid' в значении img src.
// Значение cid будет соответствовать Content-Id связанного ресурса. Таким образом, <img src='cid:barcode'>
// будет соответствовать LinkedResource с ContentId 'barcode'.
var htmlView =
    AlternateView.CreateAlternateViewFromString("Вот встроенное изображение.<img src=cid:barcode>", null,
        "text/html");

// Создайте LinkedResource (встроенное изображение) и добавьте LinkedResource в соответствующий вид.
var barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.Jpeg)
{
    ContentId = "barcode"
};

eml.LinkedResources.Add(barcode);
eml.AlternateViews.Add(plainView);
eml.AlternateViews.Add(htmlView);

eml.Save("EmbeddedImage_out.msg", SaveOptions.DefaultMsgUnicode);
```

### **Удаление встроенного изображения из тела электронной почты**

[LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) доступна через свойство [MailMessage.LinkedResources](https://reference.aspose.com/email/net/aspose.email/mailmessage/linkedresources/). Коллекция [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) предоставляет метод для полного удаления встроенных объектов, добавленных в электронное сообщение. Используйте перегруженную версию метода [LinkedResourceCollection.RemoveAt](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/removeat/#removeat/) для удаления всех следов встроенного объекта из электронного сообщения.

Примерный код ниже показывает, как удалить встроенные объекты из электронного сообщения.

```csharp
// Загрузите тестовое сообщение с связанными ресурсами
var eml = MailMessage.Load("EmlWithLinkedResources.eml");

// Удалите LinkedResource
eml.LinkedResources.RemoveAt(0, true);

// Теперь очистите альтернативный вид для связанных ресурсов
eml.AlternateViews[0].LinkedResources.Clear(true);
```
## **Работа с встроенными объектами**

Встроенный объект - это объект, который был создан в одном приложении и заключен в документ или файл, созданный другим приложением. Например, электронная таблица Microsoft Excel может быть встроена в отчет Microsoft Word, или видеофайл может быть встроен в презентацию Microsoft PowerPoint. Когда файл встраивается, а не вставляется или копируется в другой документ, он сохраняет свой оригинальный формат. Встроенный документ может быть открыт в оригинальном приложении и изменен.

### **Извлечение встроенных объектов**

Эта тема объясняет, как извлечь встроенные объекты из файла электронной почты. Встроенный документ может быть открыт в оригинальном приложении и изменен. Чтобы извлечь встроенный объект из электронного сообщения, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Загрузите файл электронной почты в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
3. Создайте цикл и создайте экземпляр класса [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) в нем.
4. Сохраните вложение и отобразите его на экране.
5. Укажите адреса отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
6. Отправьте электронную почту с помощью класса [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

Следующий фрагмент кода извлекает встроенные объекты из электронной почты.

|**Извлеченные встроенные объекты в электронной почте**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
Следующий фрагмент кода показывает, как извлечь встроенные объекты.

```csharp
var eml = MailMessage.Load("Message.msg", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.msg");
    Console.WriteLine(attachment.Name);
}
```

#### **Идентификация и извлечение встроенного вложения из формата MSG как RTF**

Для сообщений, отформатированных как RTF, следующий код может быть использован для различения и извлечения вложений, которые являются либо встроенными, либо появляются в виде иконки в теле сообщения. Следующий фрагмент кода показывает, как идентифицировать и извлечь встроенное вложение из MSG формата RTF.

```csharp

var eml = MapiMessage.Load("MSG file with RTF Formatting.msg");

foreach (var attachment in eml.Attachments)
{
    if (IsAttachmentInline(attachment))
    {
        try
        {
            SaveAttachment(attachment, Data.Out/new Guid().ToString());
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
}

static bool IsAttachmentInline(MapiAttachment attachment)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "\x0003ObjInfo")
        {
            var odtPersist1 = BitConverter.ToUInt16(property.Data, 0);
            return (odtPersist1 & (1 << (7 - 1))) == 0;
        }
    }
    return false;
}

static void SaveAttachment(MapiAttachment attachment, string fileName)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "Package")
        {
            using var fs = new FileStream(fileName, FileMode.Create, FileAccess.Write);
            fs.Write(property.Data, 0, property.Data.Length);
        }
    }
}
```

## **Извлечение вложений из подписанного электронного письма**

Подписанные электронные письма содержат одно вложение **smime.p7m**. Это означает, что электронное письмо зашифровано с использованием SMIME. Формат файла **Smime.p7m** является цифровой подписью. Чтобы увидеть содержимое этого электронного письма, используйте метод [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). Метод возвращает объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) без цифровой подписи.

```csharp
var signedEml = MailMessage.Load("signed.eml");
        
if (signedEml.IsSigned)
{
    for (var i = 0; i < signedEml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Подписанное вложение электронного письма{i}: {signedEml.Attachments[i].Name}");
    }
    
    // Электронное письмо подписано. Удалите подпись.
    var eml = signedEml.RemoveSignature();
    
    Console.WriteLine(@"Подпись удалена.");

    for (var i = 0; i < eml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Вложение электронного письма{i}: {eml.Attachments[i].Name}");
    }
}
```