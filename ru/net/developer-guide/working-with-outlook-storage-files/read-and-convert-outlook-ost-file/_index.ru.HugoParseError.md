---
title: Чтение и конвертация файлов OST Outlook
type: docs
weight: 20
url: /net/read-and-convert-outlook-ost-file/
---


Aspose.Email для .NET предоставляет API для чтения файлов OST Microsoft Outlook. Вы можете загрузить файл OST с диска или потока в экземпляр класса [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и получить информацию о его содержимом, например, папках, подпапках и сообщениях. Microsoft Outlook создает файл PST для хранения электронных писем, когда используются серверы почты POP3 или IMAP для загрузки сообщений. Он создает файл OST, когда сервером почты является Microsoft Exchange. OST поддерживает более крупные размеры файлов, чем файлы PST.

## **Чтение файлов OST**

Процесс чтения файла OST с помощью Aspose.Email точно такой же, как и для чтения файла PST. Один и тот же код может читать как файлы PST, так и OST: просто предоставьте правильное имя файла методу [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/). Следующий фрагмент кода показывает, как читать файлы OST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

## **Конвертация OST в PST**

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн с помощью бесплатного [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}
Aspose.Email позволяет конвертировать файл OST в PST всего одной строкой кода. Точно так же файл OST может быть создан из файла PST с использованием той же строки кода с перечислением [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/). В настоящее время API поддерживает конвертацию форматов OST в PST, за исключением версий 2013/2016/2019/2021 и будущих версий. Следующий фрагмент кода показывает, как конвертировать OST в PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

Для выполнения других операций с файлами OST, пожалуйста, обратитесь к следующим страницам:

- [Чтение файла PST Outlook и получение информации о папках и подпапках](https://docs.aspose.com/email/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Получение информации о сообщениях из файла PST Outlook](https://docs.aspose.com/email/net/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Извлечение сообщений из файла PST Outlook и сохранение на диск или поток в формате MSG](https://docs.aspose.com/email/net/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Доступ к информации о контактах из файла PST Outlook и сохранение на диск в формате MSG](https://docs.aspose.com/email/net/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Конвертация PST в OST**

Конвертация из PST в OST не поддерживается Aspose.Email, поскольку OST всегда создается Outlook при добавлении учетной записи и синхронизации с почтовым сервером. Разница между файлами PST и OST заключается в том, что PST доступен только локально. Содержимое OST также доступно на почтовом сервере. Поэтому нет необходимости конвертировать PST в OST для локального использования. Но вы можете импортировать PST в существующую учетную запись с помощью мастера импорта/экспорта в Outlook.