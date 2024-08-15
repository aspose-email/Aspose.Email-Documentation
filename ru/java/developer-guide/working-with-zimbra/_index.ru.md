---
title: "Работа с Zimbra"
url: /ru/java/working-with-zimbra/
weight: 110
type: docs
---

## **О Зимбре**
Zimbra — это пакет электронной почты, календаря и совместной работы, созданный для облака. Zimbra включает полный набор функций электронной почты, контактов, календаря, обмена файлами, задач, обмена сообщениями и видеоконференций, доступ к которым осуществляется через веб-клиент Zimbra с любого устройства.
## **Прочитайте все сообщения из хранилища Zimbra TGZ**
Aspose.Email предоставляет [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) класс для чтения файлов хранения Zimbra TGZ. Следующий пример кода демонстрирует использование [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) класс для чтения всех сообщений из файла. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}
## **Сохранить сообщения и структуру каталогов**
Вы также можете сохранить все сообщение со структурой каталогов из файла хранилища Zimbra TGZ. Для этого [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) класс предоставляет метод [ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) который принимает выходной путь в качестве параметра.

Следующий фрагмент кода демонстрирует использование [TgzReader.ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) метод сохранения всех сообщений из файла хранения Zimbra TGZ.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Экспорт элементов календаря и контактов из файлов резервных копий Zimbra**

Aspose.Email позволяет экспортировать календарь и контакты Zimbra в форматы iCalendar и vCard. В приведенном ниже примере кода показано, как реализовать эту функцию в нашем проекте:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.exportTo("out");
}
```