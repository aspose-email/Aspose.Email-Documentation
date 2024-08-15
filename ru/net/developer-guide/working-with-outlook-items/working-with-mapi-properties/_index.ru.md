---
title: "Работа со свойствами MAPI"
url: /ru/net/working-with-mapi-properties/
weight: 70
type: docs
---


## **Доступ к свойству Outlook MAPI и его настройка**

The [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) класс представляет собой свойство MAPI, которое содержит:

- [Name](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): строка, представляющая свойство name.
- [Tag](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): длинное значение типа, представляющее свойство тега.
- [Data](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): массив байтов, представляющий свойство данных.
 
### **Получение свойства MAPI с помощью тега свойства MAPI**

Чтобы получить свойства MAPI, выполните следующие действия:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) by [загрузка из файлов или потока](https://docs.aspose.com/email/ru/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Получите [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) from [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) by [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/) keys.

В следующем фрагменте кода показано, как получить свойство MAPI с помощью тега свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Настройка свойств MAPI**

В следующем фрагменте кода показано, как настроить свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

где определение метода convertDateTime выглядит следующим образом:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Некоторые дополнительные свойства**

В следующем фрагменте кода показано, как задать дополнительные свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Чтение именованных свойств MAPI из MSG-файлов Outlook**

Microsoft Outlook поддерживает добавление именованных свойств MAPI в файл MSG. Эти именованные свойства MAPI добавляются пользователем. Вы можете добавить именованное свойство, например «MyProp», в файл MSG с помощью Aspose.Email. Эта статья иллюстрирует возможности Aspose.Email по следующим вопросам:

- [**Доступ к свойству Outlook MAPI и его настройка**](#accessing-and-setting-outlook-mapi-property)
  - [**Получение свойства MAPI с помощью тега свойства MAPI**](#getting-mapi-property-using-the-mapi-property-tag)
  - [**Настройка свойств MAPI**](#setting-mapi-properties)
  - [**Некоторые дополнительные свойства**](#some-additional-properties)
- [**Чтение именованных свойств MAPI из MSG-файлов Outlook**](#reading-named-mapi-properties-from-outlook-msg-files)
  - [**Чтение именованных свойств MAPI из файла MSG**](#read-named-mapi-properties-from-msg-file)
  - [**Чтение именованного свойства MAPI из вложения**](#reading-named-mapi-property-from-attachment)
  - [**Удалить свойства из файлов MSG и вложений**](#remove-properties-from-msgs-and-attachments)
 
### **Чтение именованных свойств MAPI из файла MSG**

В следующем фрагменте кода показано, как читать именованные свойства MAPI из файла MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Чтение именованного свойства MAPI из вложения**

Aspose.Email также позволяет просматривать свойства [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) и найдите именованное свойство, аналогично приведенному выше примеру, для [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). В следующем фрагменте кода показано, как искать именованное свойство в коллекции свойств вложений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Удалить свойства из файлов MSG и вложений**

В следующем фрагменте кода показано, как удалить свойства из файлов MSG и вложений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}
