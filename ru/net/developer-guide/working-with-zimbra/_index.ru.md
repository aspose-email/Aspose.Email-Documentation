---
title: "Работа с Zimbra"
url: /ru/net/working-with-zimbra/
weight: 120
type: docs
---


## **О Zimbra**

Zimbra — это пакет для электронной почты, календаря и совместной работы, созданный для облака. Zimbra включает в себя полную электронную почту, контакты, календарь, файловый обмен, задачи и обмен сообщениями/видеоконференция, все это доступно через веб-клиент Zimbra с любого устройства.

## **Чтение всех сообщений из хранения Zimbra TGZ**

Aspose.Email предоставляет класс TgzReader для чтения файлов хранения Zimbra TGZ. Следующий пример кода демонстрирует использование класса TgzReader для чтения всех сообщений из файла. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}

## **Получение общего количества элементов из Tgz-файла**

Метод [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) класса [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) вернет общее количество элементарных сообщений, содержащихся в хранилище.

Следующий пример кода покажет вам, как реализовать этот метод в вашем проекте:

```cs
using (TgzReader reader = new TgzReader(fileName))
{
    int count = reader.GetTotalItemsCount();
}
```

## **Сохранение сообщений и структуры каталогов**

Вы также можете сохранить все сообщения со структурой каталогов из файла хранения Zimbra TGZ. Для этого класс TgzReader предоставляет метод ExportTo, который принимает путь для вывода в качестве параметра.

Следующий фрагмент кода демонстрирует использование метода TgzReader.ExportTo для сохранения всех сообщений из файла хранения Zimbra TGZ.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}

## **Экспорт элементов календаря и контактов из резервных файлов Zimbra**

Чтобы экспортировать календарь и контакты Zimbra и сохранить их в форматах iCalendar и VCard, вы можете использовать следующий фрагмент кода:

```cs
using (var reader = new TgzReader(@"test2.tgz"))
{
    //файлы контактов можно найти в подпапках Contacts и Emailed Contacts
    //файлы календаря можно найти в подпапке Calendar
    reader.ExportTo(@"out");
}
```