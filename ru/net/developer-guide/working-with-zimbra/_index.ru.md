---
title: "Работа с Zimbra"
url: /ru/net/working-with-zimbra/
weight: 120
type: docs
---


## **О Зимбре**

Zimbra — это пакет электронной почты, календаря и совместной работы, созданный для облака. Zimbra включает полный набор функций электронной почты, контактов, календаря, обмена файлами, задач, обмена сообщениями и видеоконференций, доступ к которым осуществляется через веб-клиент Zimbra с любого устройства.

## **Прочитайте все сообщения из хранилища Zimbra TGZ**

Aspose.Email предоставляет класс TGZReader для чтения файлов хранилища Zimbra TGZ. Следующий пример кода демонстрирует использование класса TGZReader для чтения всех сообщений из файла. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}

## **Получите общее количество элементов из файла Tgz**

The [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) метод [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) класс вернет общее количество элементов сообщения, содержащихся в хранилище.

В следующем примере кода показано, как реализовать этот метод в своем проекте:

```cs
using (TgzReader reader = new TgzReader(fileName))
{
    int count = reader.GetTotalItemsCount();
}
```

## **Сохранить сообщения и структуру каталогов**

Вы также можете сохранить все сообщение со структурой каталогов из файла хранилища Zimbra TGZ. Для этого в классе TGZReader предусмотрен метод exportTo, который принимает выходной путь в качестве параметра.

Следующий фрагмент кода демонстрирует использование метода TGZReader.exportTo для сохранения всех сообщений из файла хранилища Zimbra TGZ.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}

## **Экспорт элементов календаря и контактов из файлов Zimbra Backup**

Чтобы экспортировать календарь и контакты Zimbra и сохранить их в форматах iCalendar и vCard, вы можете использовать следующий фрагмент кода:

```cs
using (var reader = new TgzReader(@"test2.tgz"))
{
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.ExportTo(@"out");
}
```