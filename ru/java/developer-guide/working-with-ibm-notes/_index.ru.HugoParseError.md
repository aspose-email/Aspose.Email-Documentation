---
title: Работа с IBM Notes
type: docs
weight: 120
url: /java/working-with-ibm-notes/
---


## **О IBM Notes**
IBM Notes — это клиент, а IBM Domino — сервер платформы программного обеспечения для совместной работы клиент-сервер. IBM Notes предоставляет функции для совместной работы, такие как электронная почта, календари, списки задач, управление контактами и т. д. Файл базы данных, используемый IBM Notes, сохраняется в формате Notes Storage Facility (NSF).
## **Чтение сообщений из файла хранения NSF**

{{% alert color="primary" %}} 

Обратите внимание, что реализация NSF довольно ограничена.
В общем, можно столкнуться с некоторыми проблемами в следующих случаях:
 - Файл был создан версиями Notes 7 и выше
 - Используется сжатие LZ1

{{% /alert %}}

Aspose.Email предоставляет класс [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) для чтения файлов хранения NSF. Класс [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) предоставляет метод [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)), который перебирает сообщения в файле хранения NSF. Следующий пример кода демонстрирует использование класса [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) и метода [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) для чтения сообщений из файла хранения NSF.


{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}} 

Обратите внимание, что реализовано только чтение сообщений. Чтение папок пока не поддерживается из-за отсутствия спецификации.

{{% /alert %}}