---
title: "Работа с вложениями сообщений"
url: /ru/net/working-with-message-attachments/
weight: 80
type: docs
---


## **Управление вложениями с Aspose Outlook**

[Создание и сохранение файлов сообщений Outlook (MSG)](https://docs.aspose.com/email/ru/net/creating-and-saving-msg-files/) объясняет, как создавать и сохранять сообщения, а также как создавать файлы MSG с вложениями. Эта статья объясняет, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Вложения из файла сообщения получаются и сохраняются на диск с использованием свойства [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). Свойство [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) представляет собой коллекцию типа [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/).

### **Проверка, является ли вложение встроенным или обычным**

Встроенные и обычные вложения служат разным целям. Встроенные вложения визуально интегрированы в сообщение электронной почты и обычно являются изображениями или мультимедийными файлами. В то время как обычные вложения — это отдельные файлы, прикрепленные к электронной почте, и могут включать различные типы файлов. Свойство [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) класса [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) получает значение, указывающее, является ли вложение встроенным или обычным.

Следующий фрагмент кода извлекает и отображает информацию о каждом вложении в загруженном MapiMessage, включая их отображаемые имена и информацию о том, являются ли они встроенными вложениями или нет.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Сохранение вложений из файла сообщения Outlook (MSG)**

Чтобы сохранить вложения из файла MSG:

1. Переберите коллекцию [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) и получите отдельные вложения.
1. Для сохранения вложений вызовите метод Save() класса MapiAttachment.

Следующий фрагмент кода демонстрирует, как сохранить вложения на локальный диск.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Получение вложений вложенного почтового сообщения**

Встроенные OLE-вложения также появляются в коллекции вложений класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). Следующий пример кода разбирает файл сообщения на предмет встроенных вложений и сохраняет его на диск. Статический метод класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) FromProperties() может создать новое сообщение из встроенного вложения. Следующий фрагмент кода показывает, как получить вложенные почтовые сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Удаление вложений**

Библиотека Aspose Outlook предоставляет функциональность для удаления вложений из файлов сообщений Microsoft Outlook (.msg):

- Вызовите метод RemoveAttachments(). Он принимает путь к файлу сообщения в качестве параметра. Этот метод реализован как открытый статический метод, поэтому вам не нужно создавать объект.

Следующий фрагмент кода показывает, как удалить вложения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

Вы также можете вызвать статический метод класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/). Он работает быстрее, чем RemoveAttachment(), поскольку метод RemoveAttachment() разбирает файл сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Добавление вложений MSG**

Сообщение Outlook может содержать другие сообщения Microsoft Outlook в качестве вложений либо в виде обычных, либо встроенных сообщений. Коллекция [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) предоставляет перегруженные члены метода Add для создания сообщений Outlook с обоими типами вложений.

{{% alert %}}
**Попробуйте!**

Добавьте или удалите вложения электронной почты с помощью бесплатного [**Aspose.Email Editor App**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление ReferencAttachments к MapiMessage**

Метод [MapiAttachmentCollection.Add(string name, string sharedLink, string url, string providerName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) класса [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) позволяет добавлять ссылочные вложения в MapiMessage. Когда получатели электронного письма нажимают на ссылочное вложение, они могут получить доступ к связанному файлу, если у них есть соответствующие разрешения для этого. Используя ссылочное вложение, вы можете отправить меньшее сообщение электронной почты и убедиться, что у всех есть доступ к самой последней версии файла или элемента.

У метода следующие параметры:

- *name* - имя вложения
- *sharedLink* - полностью квалифицированная ссылка на вложение, предоставленная веб-сервисом, управляющим вложением
- *url* - местоположение файла
- *providerName* - имя поставщика ссылочного вложения

Пример кода ниже демонстрирует, как добавить ссылочное вложение к сообщению:

```cs
// Допустим, вы хотите отправить электронное сообщение, которое включает ссылку на файл Document.pdf, хранящийся на Google Drive.
// Вместо того, чтобы прикреплять документ непосредственно к электронному сообщению,
// вы можете создать ссылочное вложение, которое ссылается на файл на Google Drive.

// Создайте сообщение
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Файл сообщения Outlook",
    "Это сообщение создано с помощью Aspose.Email", OutlookMessageFormat.Unicode);

// Добавьте ссылочное вложение
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
//Кроме того, вы можете установить дополнительные свойства вложения
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Наконец, сохраните сообщение
msg.Save(@"my.msg");
```

### **Встраивание сообщения как вложения**

Следующий фрагмент кода показывает, как встроить вложение MSG в сообщение.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Чтение встроенных сообщений из вложений**

Следующий фрагмент кода показывает, как читать встроенные сообщения из вложений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Вставка и замена вложений**

API Aspose.Email предоставляет возможность вставлять вложения в определенный индекс в родительском сообщении. Он также предоставляет возможность заменить содержимое вложения другим вложением сообщения.

{{% alert %}}
**Попробуйте!**

Запустите простой проект приложения [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) и опробуйте возможности Aspose.Email для замены вложений в действии.
{{% /alert %}} 

### **Вставка в определенное место**

API Aspose.Email предоставляет возможность вставить вложение MSG в родительский MSG, используя метод вставки MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). Следующий фрагмент кода показывает, как вставить вложение в определенное место.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Замена содержимого вложения**

Это можно использовать для замены содержимого встроенного вложения на новые с помощью метода Replace. Однако его нельзя использовать для вставки вложения с PR_ATTACH_NUM = 4 (например) в коллекцию с collection.Count = 2. Следующий фрагмент кода показывает, как заменить содержимое вложения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Переименование вложения в MapiMessage**

Возможно редактировать значение свойства DisplayName в вложениях MapiMessage.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "Новое отображаемое имя 1";
msg.Attachments[1].DisplayName = "Новое отображаемое имя 2";
```

## **Сохранение вложений из цифровых подписанных сообщений**

API Aspose.Email предоставляет возможность получать или устанавливать значение, указывающее, будет ли декодироваться сообщение с чистой подписью.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}