---
title: "Чтение и преобразование OST-файла Outlook"
url: /ru/java/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email предоставляет API для чтения OST-файлов Microsoft Outlook. Вы можете загрузить OST-файл с диска или загрузить его в потоковом режиме в экземпляр [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях. Microsoft Outlook создает файл PST для хранения электронных писем, в которых для загрузки сообщений используются почтовые серверы POP3 или IMAP. Он создает OST-файл, когда Microsoft Exchange является почтовым сервером. OST поддерживает большие размеры файлов, чем файлы PST.

## **Чтение OST-файлов**

Процесс чтения OST-файла с помощью Aspose.Email точно такой же, как и при чтении файла PST. Один и тот же код может читать файлы PST и OST: просто укажите правильное имя файла [PersonalStorage.fromFile()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-) метод. В следующем фрагменте кода показано, как читать файлы OST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}

## **Преобразование OST в PST**

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн бесплатно [**Приложение для конвертации электронной почты Aspose.**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}
Aspose.Email позволяет конвертировать OST-файл в PST с помощью одной строки кода. Точно так же файл OST можно создать из файла PST, используя ту же строку кода, что и [FileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformat/) счетчик. В настоящее время API поддерживает преобразование форматов OST в PST, кроме OST 2013/2016. В следующем фрагменте кода показано, как конвертировать OST в PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

Для выполнения других операций с OST-файлами обратитесь к следующим страницам:

- [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Получение информации о сообщениях из файла Outlook PST](/email/java/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Извлеките сообщения из файла Outlook PST и сохраните их на диск или в потоковом режиме в формате MSG](/email/java/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Доступ к контактной информации из файла Outlook PST и сохранение на диск в формате MSG](/email/java/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Преобразование PST в OST**

Aspose.Email не поддерживает преобразование из PST в OST, поскольку OST всегда создается Outlook при добавлении учетной записи и синхронизации с почтовым сервером.
Разница между файлами PST и OST заключается в том, что PST доступен только локально. Содержимое OST также доступно на почтовом сервере.
Таким образом, нет необходимости конвертировать PST в OST для локального использования.
Но вы можете импортировать PST в существующую учетную запись с помощью мастера импорта/экспорта в Outlook.
