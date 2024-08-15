---
title: "Работа с заметками IBM"
url: /ru/net/working-with-ibm-notes/
weight: 130
type: docs
---


## **О заметках IBM**

IBM Notes является клиентом, а IBM Domino — сервером программной платформы для совместной работы клиент-сервер. IBM Notes предоставляет функции совместной работы, такие как электронная почта, календари, списки дел, управление контактами и т. д. Файл базы данных, используемый IBM Notes, сохраняется в формате Notes Storage Facility (NSF).

## **Обнаружить файл в формате NSF**

В приведенном ниже примере кода показано, как распознать формат файла NSF:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Чтение сообщений из файла хранилища NSF**

{{% alert color="primary" %}}

Обратите внимание, что реализация NSF довольно ограничена.
В целом, некоторые проблемы могут возникнуть в следующих случаях:

1. Файл был создан Notes версии 7 и выше
 
2. Используется сжатие LZ1

{{% /alert %}}

Aspose.Email предоставляет [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) класс для чтения файлов хранилища NSF. [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) класс предоставляет [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) метод, который выполняет итерацию сообщений в файле хранилища NSF. Следующий пример кода демонстрирует использование [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) класс и [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) метод чтения сообщений из файла хранилища NSF. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}}

Обратите внимание, что реализовано только чтение сообщений. Чтение папок пока не поддерживается из-за отсутствия спецификаций.

{{% /alert %}}
