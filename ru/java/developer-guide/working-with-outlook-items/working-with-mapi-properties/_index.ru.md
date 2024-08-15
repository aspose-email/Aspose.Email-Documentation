---
title: "Работа со свойствами MAPI"
url: /ru/java/working-with-mapi-properties/
weight: 60
type: docs
---

## **Настройка свойств Outlook MAPI и доступ к ним**

Aspose.Email для Java предоставляет [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) класс, представляющий свойство MAPI:

- Имя: имя свойства.
- Тег: тег свойства.
- Данные: данные об объекте недвижимости.

В этом разделе также рассматривается, как настроить свойства MAPI файла сообщений Outlook (MSG) и получить к ним доступ с помощью Aspose.Email для Java. Кроме того, был предоставлен пример кода по удалению свойств из файлов MSG и вложений.

### **Свойства чтения**

Чтобы прочитать данные свойств MAPI из файла MSG, выполните следующие действия:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс для загрузки файла MSG с использованием [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) статический метод.
2. Укажите ссылку на [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) метод получения [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Получите [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) объект из [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) от [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) keys.
4. Получите данные свойства с помощью соответствующего метода getXXX ().
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Задайте дополнительные свойства**

Следующий пример кода можно использовать для настройки дополнительных свойств Outlook [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Удалить свойства**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Чтение именованных свойств Mapi из сообщений электронной почты**

Microsoft Outlook поддерживает добавление именованных свойств MAPI в файл MSG. Эти свойства добавляются пользователем. Разработчики могут добавить именованное свойство, например «MyProp», в файл MSG с помощью Aspose.Email.

Эта статья иллюстрирует Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) коллекция для чтения именованных свойств MAPI из файла MSG.

### **Чтение именованного свойства MAPI**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Чтение именованного свойства Mapi из вложения**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}
