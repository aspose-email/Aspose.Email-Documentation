---
title: "Работа с вложениями и встроенными объектами"
url: /ru/net/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Управление вложениями электронной почты**

Вложение электронной почты — это файл, который отправляется вместе с сообщением электронной почты. Файл можно отправить как отдельное сообщение, так и как часть сообщения, к которому он прикреплен. [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс используется с [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Все сообщения содержат текст. Помимо основного текста, возможно, вы захотите отправить дополнительные файлы. Они отправляются в виде вложений и представлены в виде экземпляров [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс. Можно отправить любое количество вложений, но размер вложения ограничен почтовым сервером. Например, Gmail не поддерживает файлы размером более 10 МБ.
{{% alert %}}
**Попробуйте!**

Добавляйте или удаляйте вложения электронной почты онлайн бесплатно [**Приложение для редактирования электронной почты Aspose.Email**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление вложения**

Чтобы добавить вложение к электронному письму, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Создайте экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
1. Загрузите крепление в [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) instance.
1. Добавьте [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) экземпляр в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

В следующем фрагменте кода показано, как добавить вложение в электронное письмо.

```csharp
// Создайте экземпляр MailMessage class
var eml = new MailMessage
{
    From = "sender@from.com",
    To = "receiver@to.com",
    Subject = "This is message",
    Body = "This is body"
};

// Load an attachment
var attachment = new Attachment("1.txt");

// Add Multiple Attachment in instance of MailMessage class and Save message to disk
eml.Attachments.Add(attachment);

eml.AddAttachment(new Attachment("1.jpg"));
eml.AddAttachment(new Attachment("1.doc"));
eml.AddAttachment(new Attachment("1.rar"));
eml.AddAttachment(new Attachment("1.pdf"));
eml.Save("AddAttachments.eml");
```

Выше мы описали, как добавлять вложения в сообщение электронной почты с помощью Aspose.Email. Ниже показано, как удалять вложения и отображать информацию о них на экране.

### **Добавление справочного вложения**

Ссылочное вложение — это тип вложения, который содержит ссылку или ссылку на файл или элемент, а не сам файл или элемент в сообщении электронной почты.
Когда получатели письма нажмут на ссылочное вложение, они смогут получить доступ к связанному файлу, если у них есть на это соответствующие разрешения.
Используя вложение ссылки, вы можете отправить электронное сообщение меньшего размера и обеспечить всем доступ к самой последней версии файла или элемента.

В приведенном ниже фрагменте кода показано, как добавить справочное вложение к электронному письму. Код выполняет следующие шаги:

1. Загружает файл сообщения электронной почты с помощью [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method.
2. Создает новый объект ReferenceAttachment с именем refAttach, передавая его конструктору URL-адрес вложения «https://[attach_uri]» в качестве параметра.
3. Устанавливает имя вложения «Document.docx», используя [Name](https://reference.aspose.com/email/net/aspose.email/attachment/name/) свойство объекта refAttach.
4. Устанавливает тип поставщика вложения на [AttachmentProviderType.OneDrivePro](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) используя [ProviderType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/providertype/) свойство объекта refAttach.
5. Устанавливает тип разрешения для вложения на [AttachmentPermissionType.AnyoneCanEdit](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) используя [PermissionType](https://reference.aspose.com/email/net/aspose.email/referenceattachment/permissiontype/) свойство объекта refAttach.
6. Добавляет объект RefAttach в [Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) коллекция объекта eml с использованием [Add()](https://reference.aspose.com/email/net/aspose.email/attachmentcollection/) method.

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

Чтобы удалить вложение, выполните следующие действия:

- Создайте экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
- Грузовое крепление в случае [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) class.
- Добавьте вложение к экземпляру [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Удалите вложения из экземпляра [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс, использующий [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр класса.

В следующем фрагменте кода показано, как удалить вложение.

```csharp
// Создайте экземпляр MailMessage class
var eml = new MailMessage {From = "sender@sender.com", To = "receiver@gmail.com"};

// Load an attachment
var attachment = new Attachment("1.txt");
eml.Attachments.Add(attachment);

// Remove attachment from your MailMessage
eml.Attachments.Remove(attachment);
```

### **Отображение имени вложенного файла**

Чтобы отобразить имя вложенного файла, выполните следующие действия:

1. Просмотрите вложения в сообщении электронной почты и сохраните каждое вложение.
2. Отобразите имя каждого вложения на экране.

В следующем фрагменте кода показано, как отобразить имя вложенного файла на экране.

```csharp
var eml = MailMessage.Load("Attachments.eml");

foreach (var attachment in eml.Attachments)
{
    // Display the the attachment file name
    Console.WriteLine(attachment.Name);
}
```

### **Извлечение вложений электронной почты**

В этом разделе описывается, как извлечь вложение из файла электронной почты. Вложение электронной почты — это файл, который отправляется вместе с сообщением электронной почты. Файл можно отправить как отдельное сообщение, так и как часть сообщения, к которому он прикреплен. Все сообщения электронной почты включают возможность отправки дополнительных файлов. Они отправляются в виде вложений и представлены в виде экземпляров [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс. [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс используется с [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс по работе с вложениями. Чтобы извлечь вложения из сообщения электронной почты, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Загрузите файл электронной почты в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Создайте экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс и используйте его в цикле для извлечения всех вложений.
- Сохраните вложение и отобразите его на экране.

|**Извлеченные вложения в электронном письме**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
В следующем фрагменте кода показано, как извлекать вложения электронной почты.

```csharp
var eml = MailMessage.Load("Message.eml", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.eml");
    Console.WriteLine(attachment.Name);
}
```

#### **Извлечение описания содержимого из вложения**

Aspose.Email API предоставляет возможность читать описание содержимого вложения из заголовка вложения. В следующем фрагменте кода показано, как извлечь описание содержимого из вложения.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");
Console.WriteLine(eml.Attachments[0].Headers["Content-Description"]);
```

#### **Определение того, является ли вложение встроенным сообщением**

В следующем фрагменте кода показано, как определить, является ли вложение встроенным сообщением или нет.

```csharp
var eml = MailMessage.Load("EmailWithAttachEmbedded.eml");

Console.WriteLine(eml.Attachments[0].IsEmbeddedMessage
    ? "Attachment is an embedded message."
    : "Attachment isn't an embedded message.");
```

## **Работа со встроенными изображениями**

### **Добавить встроенное изображение в тело письма**

The [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) класс используется с [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс для встраивания объектов в сообщение электронной почты. Чтобы добавить встроенный объект, выполните следующие действия

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Укажите значения «от», «до» и «тема» в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Создайте экземпляр [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) class.
1. Создайте экземпляр [LinkedResource](https://reference.aspose.com/email/net/aspose.email/linkedresource/) class.
1. Загрузите встроенный объект в [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/).
1. Добавьте загруженный встроенный объект в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр класса.
1. Добавьте [AlternateView](https://apireference.aspose.com/email/net/aspose.email/alternateview) экземпляр к [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр класса.

Приведенные ниже фрагменты кода создают сообщение электронной почты, содержащее как обычный текст, так и текст HTML, а также изображение, встроенное в HTML.

|**Изображение, встроенное в электронную почту**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Можно отправить любое количество встроенных объектов. Размер вложения ограничен почтовым сервером. Например, Gmail не поддерживает файлы размером более 10 МБ. В приведенных ниже фрагментах кода показано, как встраивать объекты в электронное письмо.

```csharp
var eml = new MailMessage
{
    From = "AndrewIrwin@from.com",
    To = "SusanMarc@to.com",
    Subject = "This is an email"
};

// Create the plain text part It is viewable by those clients that don't support HTML
var plainView =
    AlternateView.CreateAlternateViewFromString("This is my plain text content", null, "text/plain");

// Create the HTML part.To embed images, we need to use the prefix 'cid' in the img src value.
// The cid value will map to the Content-Id of a Linked resource. Thus <img src='cid:barcode'>
// will map to a LinkedResource with a ContentId of 'barcode'.
var htmlView =
    AlternateView.CreateAlternateViewFromString("Here is an embedded image.<img src=cid:barcode>", null,
        "text/html");

// Create the LinkedResource (embedded image) and Добавьте LinkedResource to the appropriate view
var barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.Jpeg)
{
    ContentId = "barcode"
};

eml.LinkedResources.Add(barcode);
eml.AlternateViews.Add(plainView);
eml.AlternateViews.Add(htmlView);

eml.Save("EmbeddedImage_out.msg", SaveOptions.DefaultMsgUnicode);
```

### **Удалить встроенное изображение из тела письма**

[LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) доступ к которому осуществляется через [MailMessage.LinkedResources](https://reference.aspose.com/email/net/aspose.email/mailmessage/linkedresources/) имущество. Это [LinkedResourceCollection](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/) коллекция предоставляет метод полного удаления встроенных объектов, добавленных в сообщение электронной почты. Используйте перегруженную версию [LinkedResourceCollection.RemoveAt](https://reference.aspose.com/email/net/aspose.email/linkedresourcecollection/removeat/#removeat/) метод удаления всех следов встроенного объекта из сообщения электронной почты.

В приведенном ниже примере кода показано, как удалить встроенные объекты из сообщения электронной почты.

```csharp
//Load the test message with Linked Resources
var eml = MailMessage.Load("EmlWithLinkedResources.eml");

//Remove a LinkedResource
eml.LinkedResources.RemoveAt(0, true);

//Now clear the Alternate View for linked Resources
eml.AlternateViews[0].LinkedResources.Clear(true);
```
## **Работа со встроенными объектами**

Встроенный объект — это объект, созданный в одном приложении и вложенный в документ или файл, созданный другим приложением. Например, электронную таблицу Microsoft Excel можно встроить в отчет Microsoft Word, а видеофайл — в презентацию Microsoft PowerPoint. Когда файл встраивается, а не вставляется или вставляется в другой документ, он сохраняет свой исходный формат. Встроенный документ можно открыть в исходном приложении и изменить.

### **Извлечение встроенных объектов**

В этом разделе описывается, как извлечь встроенные объекты из файла электронной почты. Встроенный документ можно открыть в исходном приложении и изменить. Чтобы извлечь встроенный объект из сообщения электронной почты, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Загрузите файл электронной почты в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Создайте цикл и создайте экземпляр [Attachment](https://reference.aspose.com/email/net/aspose.email/attachment/) класс в нем.
1. Сохраните вложение и отобразите его на экране.
1. Укажите адрес отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
1. Отправка электронной почты с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class.

Приведенный ниже фрагмент кода извлекает встроенные объекты из электронного письма.

|**Извлеченные встроенные объекты в электронной почте**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
В следующем фрагменте кода показано, как извлекать встроенные объекты.

```csharp
var eml = MailMessage.Load("Message.msg", new MsgLoadOptions());

foreach (var attachment in eml.Attachments)
{
    attachment.Save("MessageEmbedded_out.msg");
    Console.WriteLine(attachment.Name);
}
```

#### **Определите и извлеките встроенное вложение из MSG в формате RTF**

Для сообщений, отформатированных как RTF, следующий код можно использовать для различения и извлечения вложений, которые находятся в строке или отображаются в виде значка в теле сообщения. В следующем фрагменте кода показано, как идентифицировать и извлечь встроенное вложение из файла MSG в формате RTF.

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

## **Получение вложений из подписанного электронного письма**

Подписанные письма содержат одно **smime.p7m** вложение. Это означает, что электронное письмо зашифровано с помощью SMIME. **Smime.p7m** формат файла — цифровая подпись.
Чтобы увидеть содержимое этого письма, используйте [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/) метод. Метод возвращает [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект без цифровой подписи.

```csharp
var signedEml = MailMessage.Load("signed.eml");
       
if (signedEml.IsSigned)
{
    for (var i = 0; i < signedEml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Signed email attachment{i}: {signedEml.Attachments[i].Name}");
    }
   
    // The email is signed. Remove a signature.
    var eml = signedEml.RemoveSignature();
   
    Console.WriteLine(@"Signature removed.");

    for (var i = 0; i < eml.Attachments.Count; i++)
    {
        Console.WriteLine($@"Email attachment{i}: {eml.Attachments[i].Name}");
    }
}
```
