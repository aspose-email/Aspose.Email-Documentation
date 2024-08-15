---
title: "Чтение и преобразование OST-файла Outlook"
url: /ru/net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email для .NET предоставляет API для чтения OST-файлов Microsoft Outlook. Вы можете загрузить OST-файл с диска или потока в экземпляр [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях. Microsoft Outlook создает файл PST для хранения электронных писем, когда для загрузки сообщений используются почтовые серверы POP3 или IMAP. Он создает OST-файл, когда Microsoft Exchange является почтовым сервером. OST поддерживает большие размеры файлов, чем файлы PST.

## **Чтение OST-файлов**

Процесс чтения OST-файла с помощью Aspose.Email точно такой же, как и при чтении файла PST. Один и тот же код может читать файлы PST и OST: просто укажите правильное имя файла [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/) метод. В следующем фрагменте кода показано, как читать файлы OST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

## **Преобразование OST в PST**

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн бесплатно [**Приложение для конвертации электронной почты Aspose.**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}
Aspose.Email позволяет конвертировать OST-файл в PST с помощью одной строки кода. Точно так же файл OST можно создать из файла PST, используя ту же строку кода, что и [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/) счетчик. В настоящее время API поддерживает преобразование форматов OST в PST, кроме 2013/2016/2019/2021 и будущих версий. В следующем фрагменте кода показано, как конвертировать OST в PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

Для выполнения других операций с OST-файлами обратитесь к следующим страницам:

- [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](https://docs.aspose.com/email/ru/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Получение информации о сообщениях из файла Outlook PST](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Извлеките сообщения из файла Outlook PST и сохраните их на диск или в потоковом режиме в формате MSG](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Доступ к контактной информации из файла Outlook PST и сохранение на диск в формате MSG](https://docs.aspose.com/email/ru/net/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Преобразование PST в OST**

Aspose.Email не поддерживает преобразование из PST в OST, поскольку OST всегда создается Outlook при добавлении учетной записи и синхронизации с почтовым сервером.
Разница между файлами PST и OST заключается в том, что PST доступен только локально. Содержимое OST также доступно на почтовом сервере.
Таким образом, нет необходимости конвертировать PST в OST для локального использования.
Но вы можете импортировать PST в существующую учетную запись с помощью мастера импорта/экспорта в Outlook.
