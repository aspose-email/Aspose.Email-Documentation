---
title: "Работа с вложениями сообщений"
url: /ru/net/working-with-message-attachments/
weight: 80
type: docs
---


## **Управление вложениями с помощью Aspose Outlook**

[Создание и сохранение файлов сообщений Outlook (MSG)](https://docs.aspose.com/email/ru/net/creating-and-saving-msg-files/) объясняет, как создавать и сохранять сообщения, а также как создавать файлы MSG с вложениями. В этой статье объясняется, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Доступ к вложениям из файла сообщений и их сохранение на диск осуществляется с помощью [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) имущество. Это [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) свойство представляет собой набор типов [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) class.

### **Проверьте, является ли вложение встроенным или обычным**

Встроенные и обычные насадки служат разным целям. Встроенные вложения визуально интегрированы в сообщение электронной почты и обычно представляют собой изображения или медиафайлы. Между тем, обычные вложения представляют собой отдельные файлы, прикрепленные к электронному письму, и могут включать различные типы файлов. [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) собственность [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class получает значение, указывающее, является ли вложение встроенным или обычным.

В следующем примере кода извлекается и отображается информация о каждом вложении в загруженном MAPIMessage, включая их отображаемые имена и сведения о том, являются ли они встроенными вложениями или нет.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Сохранить вложения из файла сообщений Outlook (MSG)**

Чтобы сохранить вложения из файла MSG, выполните следующие действия:

1. Пройдите итерацию через [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) соберите и получите отдельные вложения.
1. Чтобы сохранить вложения, вызовите метод Save () класса MapiAttachment.

В следующем фрагменте кода показано, как сохранять вложения на локальный диск.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Получение вложений вложенных почтовых сообщений**

Встроенные вложения OLE также отображаются в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс «Коллекция вложений». В следующем примере кода файл сообщений анализируется на наличие вложенных сообщений и сохраняется на диске. [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) статический метод class FromProperties () может создать новое сообщение из встроенного вложения. В следующем фрагменте кода показано, как получать вложенные вложения в почтовые сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Удаление вложений**

Библиотека Aspose Outlook предоставляет возможность удаления вложений из файлов сообщений Microsoft Outlook (.msg):

- Вызовите метод removeAttachments (). В качестве параметра он принимает путь к файлу сообщения. Он реализован как публичный статический метод, поэтому вам не нужно создавать экземпляр объекта.

В следующем фрагменте кода показано, как удалить вложения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

Вы также можете позвонить в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) статический метод класса [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/). Он работает быстрее, чем removeAttachment (), поскольку метод removeAttachment () анализирует файл сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Добавление вложений MSG**

Сообщение Outlook может содержать другие сообщения Microsoft Outlook во вложениях в виде обычных или встроенных сообщений. [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) предоставляет перегруженным участникам метода Add возможность создавать сообщения Outlook с обоими типами вложений.

{{% alert %}}
**Попробуйте!**

Добавляйте или удаляйте вложения электронной почты бесплатно [**Приложение для редактирования электронной почты Aspose.Email**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление справочного вложения в сообщение MapiMessage**

The [MAPIattachmentCollection.add (строковое имя, строка SharedLink, URL-адрес строки, имя поставщика строки)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) метод [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) класс позволяет добавить ссылочное вложение в MapiMessage. Когда получатели письма нажмут на ссылочное вложение, они смогут получить доступ к связанному файлу, если у них есть на это соответствующие разрешения. Используя вложение ссылки, вы можете отправить электронное сообщение меньшего размера и обеспечить всем доступ к самой последней версии файла или элемента.

Метод имеет следующие параметры:

- *name* - имя вложения
- *sharedLink* - полная общедоступная ссылка на вложение, предоставленная веб-сервисом, манипулирующим вложением
- *url* - местоположение файла
- *providerName* - имя поставщика эталонных вложений

В приведенном ниже примере кода показано, как добавить к сообщению справочное вложение:

```cs
// Let's say you want to send an email message that includes a link to a Document.pdf file stored on a Google Drive.
// Instead of attaching the document directly to the email message,
// you can create a reference attachment that links to the file on the Google Drive.

// Create a message
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Outlook message file",
    "This message is created by Aspose.Email", OutlookMessageFormat.Unicode);

// Add reference attachment
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
//Also, you can set additional attachment properties
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Finally save the message
msg.Save(@"my.msg");
```

### **Встраивание сообщения в виде вложения**

В следующем фрагменте кода показано, как встроить вложенный файл MSG в сообщение.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Чтение встроенных сообщений из вложений**

В следующем фрагменте кода показано, как читать встроенные сообщения из вложений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Установка и замена навесного оборудования**

Aspose.Email API предоставляет возможность вставлять вложения в определенном индексе в родительское сообщение. Он также предоставляет возможность заменять содержимое вложения другим вложением сообщения.

{{% alert %}}
**Попробуйте!**

Запустите [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) простой проект приложения и попробуйте возможности Aspose.Email для замены вложений в действии.
{{% /alert %}}

### **Вставить в определенном месте**

API Aspose.Email предоставляет возможность вставлять вложение MSG в родительское сообщение с помощью метода вставки MapiAttachmentCollection Insert (индекс int, строковое имя, сообщение MapiMessage). В следующем фрагменте кода показано, как вставить вложение в определенное место.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Заменить содержимое вложения**

Это можно использовать для замены содержимого встроенного вложения новым с помощью метода Replace. Однако его нельзя использовать для вставки вложений с PR_ATTACH_NUM = 4 (например) в коллекцию с Collection.count = 2. В следующем фрагменте кода показано, как заменить содержимое вложения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Переименование вложения в MAPImessage**

Можно изменить значение свойства DisplayName во вложениях MapiMessage.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "New display name 1";
msg.Attachments[1].DisplayName = "New display name 2";
```

## **Сохраняйте вложения из сообщений с цифровой подписью**

Aspose.Email API предоставляет возможность получить или установить значение, указывающее, будет ли декодировано сообщение с четкой подписью. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}
