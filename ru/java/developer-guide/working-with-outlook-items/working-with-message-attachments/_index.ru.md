---
title: "Работа с вложениями сообщений"
url: /ru/java/working-with-message-attachments/
weight: 70
type: docs
---

## **Разбор и сохранение вложений**

Файлы сообщений Outlook могут содержать одно или несколько вложений. Aspose.Email позволяет разработчикам просматривать вложения в MSG-файле и сохранять их на диске. В этом разделе описывается процесс. В нем также описано, как вставить вложение.

Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс используется для загрузки файла MSG с диска и предоставляет [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) метод, который ссылается на [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) коллекция объектов, связанная с файлом MSG. [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) объект также предоставляет методы, выполняющие действия с вложением.

Чтобы сохранить вложения в файле MSG на диск с оригинальным именем и расширением, выполните следующие действия:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс для загрузки файла MSG с использованием [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) статический метод.
2. Позвоните [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) class [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) метод получения ссылки на коллекцию [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) объекты, связанные с файлом MSG.
3. Пройдите через [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) для отображения содержимого каждого [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) объект с помощью публичных методов.
4. Позвоните [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) class [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) метод сохранения вложения на диск.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Встраивание сообщений в виде вложений

Сообщение Microsoft Outlook может содержать другие сообщения Microsoft Outlook во вложениях в виде обычных сообщений, описанных выше, или встроенных сообщений. [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/)  предоставляет перегруженным участникам метода add для создания сообщений Outlook с обоими типами вложений. Файлы MSG Outlook, встроенные в файл MSG, содержат метод PR_ATTACH_METHOD со значением 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Чтение встроенного сообщения из вложения**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Вложения MSG: вставка и замена**

Aspose.Email API предоставляет возможность вставлять вложения в определенном индексе в родительское сообщение. Он также предоставляет возможность заменять содержимое вложения другим вложением сообщения.

### **Вставьте вложение MSG в определенное место**

Aspose.Email API предоставляет возможность вставлять вложение MSG в родительское сообщение с помощью [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-) method.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Замените содержимое встроенных вложений MSG**

Это можно использовать для замены содержимого встроенного вложения новым, используя [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-) метод. Однако его нельзя использовать для вставки вложения с PR_ATTACH_NUM = 4 (например) в коллекцию с Collection.count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Сохранение вложений из сообщения с цифровой подписью**

Aspose.Email API предоставляет возможность получить или установить значение, указывающее, будет ли декодировано сообщение с четкой подписью. 

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Переименовать вложение в MAPIMessage**

Aspose.Email позволяет редактировать [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) стоимость недвижимости в [Вложения MAPImessage](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

В следующем примере кода показано, как обновить отображаемые имена первого и второго вложений в загруженном сообщении Mapi:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("New display name 1");
msg.getAttachments().get_Item(1).setDisplayName("New display name 2");
```
## **Проверьте, является ли вложение встроенным или обычным**

Разница между встроенными и обычными вложениями заключается в том, как они представлены в электронном письме. Встроенные вложения встроены в текст письма, и их можно просматривать без необходимости открывать отдельный файл или скачивать что-либо. С другой стороны, обычные вложения — это отдельные файлы, которые вложены в электронное письмо, но не отображаются непосредственно в тексте сообщения и должны быть загружены и открыты извне. [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) собственность [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) class получает значение, указывающее, является ли вложение встроенным или обычным.

Следующий пример кода загружает сообщение электронной почты из файла, а затем извлекает информацию о вложениях, в частности печатает отображаемое имя каждого вложения и указано, находится ли оно в сообщении или нет:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```

