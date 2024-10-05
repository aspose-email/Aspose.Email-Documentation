---
title: "Чтение и преобразование файла Outlook OST"
url: /ru/java/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email предоставляет API для чтения файлов Microsoft Outlook OST. Вы можете загрузить файл OST с диска или потока в экземпляр класса [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и получить информацию о его содержимом, например, о папках, подпапках и сообщениях. Microsoft Outlook создает файл PST для хранения электронных писем, когда используются почтовые серверы POP3 или IMAP для загрузки сообщений. Он создает файл OST, когда сервером электронной почты является Microsoft Exchange. OST поддерживает больший размер файлов, чем PST.

## **Чтение файлов OST**

Процесс чтения файла OST с помощью Aspose.Email точно такой же, как и для чтения файла PST. Тот же код может читать как файлы PST, так и OST: просто укажите правильное имя файла в методе [PersonalStorage.fromFile()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-). Следующий фрагмент кода показывает, как читать файлы OST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}

## **Преобразование OST в PST**

{{% alert %}}
**Попробуйте это!**

Преобразуйте электронные письма и архивы сообщений онлайн с помощью бесплатного [**Приложения для преобразования Aspose.Email**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}
Aspose.Email позволяет преобразовать файл OST в PST с помощью одной строки кода. Аналогично, файл OST может быть создан из файла PST с использованием той же строки кода с перечислением [FileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformat/). В настоящее время API поддерживает преобразование форматов OST в PST, кроме OST 2013/2016. Следующий фрагмент кода показывает, как преобразовать OST в PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

Для выполнения других операций с файлами OST, пожалуйста, обратитесь к следующим страницам:

- [Чтение файла Outlook PST и получение информации о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Получение информации о сообщениях из файла Outlook PST](/email/java/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Извлечение сообщений из файла Outlook PST и сохранение на диск или поток в формате MSG](/email/java/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Доступ к контактной информации из файла Outlook PST и сохранение на диск в формате MSG](/email/java/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Преобразование PST в OST**

Преобразование из PST в OST не поддерживается Aspose.Email, поскольку OST всегда создается Outlook при добавлении учетной записи и синхронизации с почтовым сервером. Разница между файлами PST и OST в том, что PST доступен только локально. Содержимое OST также доступно на почтовом сервере. Поэтому нет необходимости преобразовывать PST в OST для локального использования. Но вы можете импортировать PST в существующую учетную запись с помощью мастера импорта/экспорта в Outlook.