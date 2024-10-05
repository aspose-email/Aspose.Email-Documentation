---
title: Работа с Zimbra
type: docs
weight: 110
url: /java/working-with-zimbra/
---

## **О Zimbra**
Zimbra - это набор инструментов для электронной почты, календаря и совместной работы, созданный для облака. Zimbra включает в себя полноценные функции электронной почты, контактов, календаря, совместного использования файлов, задач и обмена сообщениями/видеоконференций, доступные через веб-клиент Zimbra с любого устройства.
## **Чтение всех сообщений из хранилища Zimbra TGZ**
Aspose.Email предоставляет класс [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) для чтения файлов хранилища Zimbra TGZ. Приведенный ниже образец кода демонстрирует использование класса [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) для чтения всех сообщений из файла.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}
## **Сохранение сообщений и структуры каталогов**
Вы также можете сохранить все сообщения с сохранением структуры каталогов из файла хранилища Zimbra TGZ. Для этого класс [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) предоставляет метод [ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)), который принимает путь к выходному файлу в качестве параметра.

Приведенный ниже фрагмент кода демонстрирует использование метода [TgzReader.ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) для сохранения всех сообщений из файла хранилища Zimbra TGZ.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Экспорт элементов календаря и контактов из резервных файлов Zimbra**

Aspose.Email позволяет экспортировать календари и контакты Zimbra в форматы iCalendar и VCard. Приведенный ниже пример кода показывает, как реализовать эту функцию в нашем проекте:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //файлы контактов можно найти в подпапках Contacts и Emailed Contacts
    //файлы календаря можно найти в подпапке Calendar
    reader.exportTo("out");
}
```