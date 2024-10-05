---
title: Работа с MAPI-свойствами
type: docs
weight: 70
url: /net/working-with-mapi-properties/
---


## **Доступ и установка свойств MAPI Outlook**

Класс [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) представляет собой свойство MAPI, которое содержит:

- [Имя](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): строка, представляющая имя свойства.
- [Тег](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): значение типа long, представляющее тег свойства.
- [Данные](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): массив байтов, представляющий данные свойства.
  
### **Получение свойства MAPI с использованием тега свойства MAPI**

Чтобы получить свойства MAPI:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с [загрузкой из файлов или потока](https://docs.aspose.com/email/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Получите [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) из [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) по ключам [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/).

Следующий фрагмент кода показывает, как получить свойство MAPI с использованием тега свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Установка свойств MAPI**

Следующий фрагмент кода показывает, как установить свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

где определение метода convertDateTime выглядит следующим образом:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Некоторые дополнительные свойства**

Следующий фрагмент кода показывает, как установить дополнительные свойства MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Чтение именованных свойств MAPI из файлов MSG Outlook**

Microsoft Outlook поддерживает добавление именованных свойств MAPI в файл MSG. Эти именованные свойства MAPI добавляются пользователем. Вы можете добавить именованное свойство, например, "MyProp", в файл MSG с помощью Aspose.Email. Эта статья иллюстрирует возможности Aspose.Email:

- [**Доступ и установка свойств MAPI Outlook**](#accessing-and-setting-outlook-mapi-property)
  - [**Получение свойства MAPI с использованием тега свойства MAPI**](#getting-mapi-property-using-the-mapi-property-tag)
  - [**Установка свойств MAPI**](#setting-mapi-properties)
  - [**Некоторые дополнительные свойства**](#some-additional-properties)
- [**Чтение именованных свойств MAPI из файлов MSG Outlook**](#reading-named-mapi-properties-from-outlook-msg-files)
  - [**Читать именованные свойства MAPI из файла MSG**](#read-named-mapi-properties-from-msg-file)
  - [**Чтение именованного свойства MAPI из вложения**](#reading-named-mapi-property-from-attachment)
  - [**Удалить свойства из MSG и вложений**](#remove-properties-from-msgs-and-attachments)
  
### **Читать именованные свойства MAPI из файла MSG**

Следующий фрагмент кода показывает, как читать именованные свойства MAPI из файла MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Чтение именованного свойства MAPI из вложения**

Aspose.Email также позволяет вам проходить через свойства [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) и искать именованное свойство, аналогично приведенному выше примеру для [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). Следующий фрагмент кода показывает, как искать именованное свойство через коллекцию свойств вложения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Удалить свойства из MSG и вложений**

Следующий фрагмент кода показывает, как удалить свойства из MSG и вложений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}