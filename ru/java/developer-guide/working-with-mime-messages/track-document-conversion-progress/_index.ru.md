---
title: "Отслеживание прогресса конверсии документа"
url: /ru/java/track-document-conversion-progress/
weight: 60
type: docs
---

## **Отслеживание прогресса конверсии документа**

Aspose.Email предоставляет возможность отслеживать прогресс конверсии документа. Для этого API предоставляет [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/#getCustomProgressHandler--), который представляет метод, обрабатывающий события прогресса. Типы событий прогресса представлены перечислением [ProgressEventType](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/). Перечисление **ProgressEventType** имеет следующие члены.

- [MimeStructureCreated](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimeStructureCreated): Это событие сообщает, что структура MIME создана.
- [MimePartSaved](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimePartSaved): Это событие сообщает, что сохранение одной части MIME завершено.
- [SavedToStream](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#SavedToStream): Это событие сообщает, что все части MIME сохранены в поток.

Следующий пример кода демонстрирует использование **SaveOptions.CustomProgressHandler** и перечисления **ProgressEventType** для отслеживания прогресса конверсии документа.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-1.java" >}}

Следующий код представляет собой код для настраиваемого класса, использованного в примере кода, приведенном выше.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-2.java" >}}