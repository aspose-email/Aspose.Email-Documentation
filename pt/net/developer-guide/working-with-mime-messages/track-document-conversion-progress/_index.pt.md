---
title: "Acompanhar o Progresso da Conversão de Documentos"
url: /pt/net/track-document-conversion-progress/
weight: 60
type: docs
---

Aspose.Email fornece a funcionalidade de acompanhar o progresso da conversão de documentos. Para isso, a API fornece [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/). que representa o método que trata os eventos de progresso. Os tipos de eventos de progresso são representados pela enumeração [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/). A enumeração [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) possui os seguintes membros.

- MimeStructureCreated: Este evento informa que a estrutura MIME foi criada.  
- MimePartSaved: Este evento informa que o salvamento de uma parte MIME foi concluído.  
- SavedToStream: Este evento informa que todas as partes MIME foram salvas no stream.  

O seguinte código de exemplo demonstra o uso de [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) e da enumeração [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) para acompanhar o progresso da conversão de documentos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

O seguinte é o código para a classe personalizada usada no código de exemplo fornecido acima.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}