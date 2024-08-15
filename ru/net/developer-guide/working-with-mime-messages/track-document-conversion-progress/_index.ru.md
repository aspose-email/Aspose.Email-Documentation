---
title: "Отслеживайте прогресс преобразования документов"
url: /ru/net/track-document-conversion-progress/
weight: 60
type: docs
---


Aspose.Email предоставляет возможность отслеживать процесс преобразования документов. Для этого API предоставляет [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/). который представляет собой метод обработки событий прогресса. Типы событий прогресса представлены в виде [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) перечисление. [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) перечисление состоит из следующих членов.

- MIMEStructureCreated: это событие сообщает о создании структуры MIME.
- MimePartSaved: это событие сообщает, что сохранение одной части MIME завершено.
- SavedToStream: это событие сообщает, что все части мима сохранены в потоковом режиме.

Следующий пример кода демонстрирует использование [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) and [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) перечисление отслеживайте прогресс преобразования документов.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

Ниже приведен код пользовательского класса, использованный в приведенном выше примере кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}
