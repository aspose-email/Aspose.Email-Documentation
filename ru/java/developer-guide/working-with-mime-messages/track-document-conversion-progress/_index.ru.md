---
title: "Отслеживайте прогресс преобразования документов"
url: /ru/java/track-document-conversion-progress/
weight: 60
type: docs
---

## **Отслеживайте прогресс преобразования документов**

Aspose.Email предоставляет возможность отслеживать процесс преобразования документов. Для этого API предоставляет [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/#getCustomProgressHandler--). который представляет собой метод обработки событий прогресса. Типы событий прогресса представлены в виде [ProgressEventType](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/) перечисление. **ProgressEventType** перечисление состоит из следующих членов.

- [MimeStructureCreated](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimeStructureCreated): Это событие сообщает о создании структуры MIME.
- [MimePartSaved](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimePartSaved): Это событие сообщает, что сохранение одной части пантомимы завершено.
- [SavedToStream](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#SavedToStream): Это событие сообщает, что все партии MIME сохранены в потоковом режиме.

Следующий пример кода демонстрирует использование **SaveOptions.CustomProgressHandler** and **ProgressEventType** перечисление отслеживайте прогресс преобразования документов.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-1.java" >}}

Ниже приведен код пользовательского класса, использованный в приведенном выше примере кода.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-2.java" >}}
