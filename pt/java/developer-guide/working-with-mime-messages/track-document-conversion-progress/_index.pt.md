---
title: "Acompanhar o Progresso da Conversão de Documentos"
url: /pt/java/track-document-conversion-progress/
weight: 60
type: docs
---

## **Acompanhar o Progresso da Conversão de Documentos**

Aspose.Email fornece a possibilidade de acompanhar o progresso da conversão de documentos. Para isso, a API fornece [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/#getCustomProgressHandler--), que representa o método que lida com os eventos de progresso. Os tipos de eventos de progresso são representados pela enumeração [ProgressEventType](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/). A enumeração **ProgressEventType** possui os seguintes membros.

- [MimeStructureCreated](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimeStructureCreated): Este evento informa que a estrutura mime foi criada.
- [MimePartSaved](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimePartSaved): Este evento informa que o salvamento de uma parte mime foi concluído.
- [SavedToStream](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#SavedToStream): Este evento informa que todas as partes mime foram salvas no fluxo.

O seguinte código de exemplo demonstra o uso de **SaveOptions.CustomProgressHandler** e a enumeração **ProgressEventType** para acompanhar o progresso da conversão de documentos.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-1.java" >}}

O seguinte é o código da classe personalizada utilizada no exemplo de código dado acima.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-2.java" >}}