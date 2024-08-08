---
title: Track Document Conversion Progress
type: docs
weight: 60
url: /net/track-document-conversion-progress/
---


Aspose.Email provides the facility to track the document conversion progress. For this, the API provides [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/). which represents the method that handles the progress events. The progress event types are represented by the [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) enumeration. The [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) enumeration has the following members.

- MimeStructureCreated: This event informs that the mime structure is created.
- MimePartSaved: This event informs that saving of one mime part is finished.
- SavedToStream: This event informs that all mime parts are saved to stream.

The following sample code demonstrates the use of [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) and [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) enumeration track the document conversion progress.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

The following is the code for the custom class used in the code sample given above.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}
