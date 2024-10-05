---
title: "Работа с вложениями сообщений"
url: /ru/java/working-with-message-attachments/
weight: 70
type: docs
---

## **Разбор и сохранение вложений**

Файлы сообщений Outlook могут содержать одно или несколько вложений. Aspose.Email позволяет разработчикам проходить по вложениям в файле MSG и сохранять их на диск. Эта тема описывает процесс. Также описывается, как встроить вложение.

Класс Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) используется для загрузки файла MSG с диска и предоставляет метод [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--), который ссылается на коллекцию объектов [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/), связанных с файлом MSG. Объект [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) дополнительно предоставляет методы, которые выполняют действия с вложением.

Чтобы сохранить вложения в файле MSG на диск с оригинальным именем и расширением:

1. Создайте экземпляр класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), чтобы загрузить файл MSG, используя статический метод [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Вызовите метод [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) класса [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/), чтобы получить ссылку на коллекцию объектов [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/), связанных с файлом MSG.
3. Пройдите в цикле по [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/), чтобы отобразить содержание каждого объекта [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) через его публичные методы.
4. Вызовите метод [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) класса [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/), чтобы сохранить вложение на диск.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Встраивание сообщений как вложений

Сообщение Microsoft Outlook может содержать другие сообщения Microsoft Outlook во вложениях либо в виде обычных сообщений, описанных выше, либо встроенных сообщений. Коллекция [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) предоставляет перегруженные члены метода add для создания сообщений Outlook с обоими типами вложений. Вложенные в файл MSG сообщения содержат PR_ATTACH_METHOD со значением 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Чтение встроенного сообщения из вложения**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Вставка и замена вложений MSG**

API Aspose.Email предоставляет возможность вставлять вложения по определенному индексу в родительском сообщении. Он также предоставляет возможность замены содержимого вложения другим вложением.

### **Вставить вложение MSG в конкретное место**

API Aspose.Email предоставляет возможность вставить вложение MSG в родительский MSG, используя метод [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-).

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Заменить содержимое встроенного вложения MSG**

Это можно использовать для замены содержимого встроенного вложения новыми, используя метод [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-). Однако, его нельзя использовать для вставки вложения с PR_ATTACH_NUM = 4 (например) в коллекцию с collection.Count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Сохранение вложений из цифрово подписанного сообщения**

API Aspose.Email предоставляет возможность получить или установить значение, указывающее будет ли расшифровываться ясно подписанное сообщение.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Переименование вложения в MapiMessage**

Aspose.Email позволяет редактировать значение свойства [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) в вложениях [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

Следующий пример кода демонстрирует, как обновить имена дисплеев первых и вторых вложений в загруженном сообщении Mapi:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("Новое имя дисплея 1");
msg.getAttachments().get_Item(1).setDisplayName("Новое имя дисплея 2");
```

## **Проверка, является ли вложение встроенным или обычным**

Разница между встроенными и обычными вложениями заключается в том, как они представлены в электронном письме. Встроенные вложения встраиваются в тело письма и могут быть просмотрены без необходимости открывать отдельный файл или что-либо загружать. Обычные вложения, с другой стороны, являются отдельными файлами, прикрепленными к письму, но не отображаются непосредственно в теле сообщения и должны быть загружены и открыты отдельно. Свойство [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) класса [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) получает значение, указывающее, является ли вложение встроенным или обычным.

Следующий пример кода загружает сообщение электронной почты из файла и затем извлекает информацию о вложениях, в частности, выводит имя дисплея каждого вложения и является ли оно встроенным в сообщение или нет:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```