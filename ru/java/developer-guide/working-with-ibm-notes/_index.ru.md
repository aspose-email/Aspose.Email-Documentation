---
title: "Работа с заметками IBM"
url: /ru/java/working-with-ibm-notes/
weight: 120
type: docs
---


## **О заметках IBM**
IBM Notes является клиентом, а IBM Domino — сервером программной платформы для совместной работы клиент-сервер. IBM Notes предоставляет функции совместной работы, такие как электронная почта, календари, списки дел, управление контактами и т. д. Файл базы данных, используемый IBM Notes, сохраняется в формате Notes Storage Facility (NSF).
## **Чтение сообщений из файла хранилища NSF**

{{% alert color="primary" %}}

Обратите внимание, что реализация NSF довольно ограничена.
В целом, некоторые проблемы могут возникнуть в следующих случаях:
 - Файл был создан Notes версии 7 и выше
 - Используется сжатие LZ1

{{% /alert %}}

Aspose.Email предоставляет [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) класс для чтения файлов хранилища NSF. [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) класс предоставляет [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) метод, который выполняет итерацию сообщений в файле хранилища NSF. Следующий пример кода демонстрирует использование [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) класс и [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) метод чтения сообщений из файла хранилища NSF. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}}

Обратите внимание, что реализовано только чтение сообщений. Чтение папок пока не поддерживается из-за отсутствия спецификаций.

{{% /alert %}}
