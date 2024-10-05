---
title: "Работа с MAPI-свойствами"
url: /ru/java/working-with-mapi-properties/
weight: 60
type: docs
---

## **Установка и доступ к MAPI-свойствам Outlook**

Aspose.Email для Java предоставляет класс [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/), который представляет MAPI-свойство:

- Имя: имя свойства.
- Тег: тег свойства.
- Данные: данные свойства.

В этой теме также обсуждается, как установить и получить доступ к MAPI-свойствам файла сообщения Outlook (MSG) с использованием Aspose.Email для Java. Кроме того, предоставлен пример кода о том, как удалить свойства из MSG и вложений.

### **Чтение свойств**

Чтобы прочитать данные MAPI-свойств из MSG-файла:

1. Создайте экземпляр класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), чтобы загрузить MSG-файл, используя статический метод [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Установите ссылку на объект [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) метода [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) для получения [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Получите объект [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) из [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) по ключам [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/).
4. Получите данные свойства с использованием соответствующего метода getXXX().
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Установка дополнительных свойств**

Следующий пример кода можно использовать для установки дополнительных свойств сообщения Outlook [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Удаление свойств**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Чтение именованных Mapi-свойств из сообщений электронной почты**

Microsoft Outlook поддерживает добавление именованных MAPI-свойств в MSG-файл. Эти свойства добавляются пользователем. Разработчики могут добавить именованное свойство, например, “MyProp”, в MSG-файл с использованием Aspose.Email.

В этой статье иллюстрируется Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) коллекция [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) для чтения именованных MAPI-свойств из MSG-файла.

### **Чтение именованного MAPI-свойства**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Чтение именованного Mapi-свойства из вложения**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}