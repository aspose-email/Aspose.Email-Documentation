---
title: Отслеживание Прогресса Конвертации Документов
type: docs
weight: 60
url: /net/track-document-conversion-progress/
---


Aspose.Email предоставляет возможность отслеживать прогресс конвертации документов. Для этого API предоставляет [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/), который представляет метод, обрабатывающий события прогресса. Типы событий прогресса представлены перечислением [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/). Перечисление [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) имеет следующие члены.

- MimeStructureCreated: Это событие информирует о том, что MIME-структура создана.
- MimePartSaved: Это событие информирует о том, что сохранение одной части MIME завершено.
- SavedToStream: Это событие информирует о том, что все части MIME сохранены в поток.

Следующий пример кода демонстрирует использование [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) и перечисления [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) для отслеживания прогресса конвертации документов.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

Следующий код предназначен для пользовательского класса, используемого в приведенном выше примере кода.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}