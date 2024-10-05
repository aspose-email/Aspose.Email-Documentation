---
title: Работа с IBM Notes
type: docs
weight: 130
url: /net/working-with-ibm-notes/
---


## **О IBM Notes**

IBM Notes - это клиент, а IBM Domino - сервер коллаборативной клиент-серверной программной платформы. IBM Notes предоставляет функции совместной работы, такие как электронная почта, календари, списки задач, управление контактами и др. Файл базы данных, используемый IBM Notes, сохраняется в формате Notes Storage Facility (NSF).

## **Определение формата файла NSF**

Пример кода ниже покажет вам, как распознать формат файла NSF:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Чтение сообщений из файла хранилища NSF**

{{% alert color="primary" %}}

Обратите внимание, что реализация NSF довольно ограничена.
В целом, можно столкнуться с некоторыми проблемами в следующих случаях:

1. Файл был создан в версии Notes 7 или выше
  
2. Используется сжатие LZ1

{{% /alert %}}

Aspose.Email предоставляет класс [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) для чтения файлов хранилища NSF. Класс [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) предоставляет метод [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages), который перебирает сообщения в файле хранилища NSF. Приведённый ниже пример кода демонстрирует использование класса [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) и метода [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) для чтения сообщений из файла хранилища NSF.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}} 

Обратите внимание, что реализовано только чтение сообщений. Чтение папок пока не поддерживается из-за отсутствия спецификации.

{{% /alert %}}