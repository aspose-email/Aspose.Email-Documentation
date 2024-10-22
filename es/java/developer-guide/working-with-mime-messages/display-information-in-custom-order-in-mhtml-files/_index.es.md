---
title: "Mostrar información en un orden personalizado en archivos MHTML"
url: /es/java/display-information-in-custom-order-in-mhtml-files/
weight: 80
type: docs
---

Aspose.Email proporciona la propiedad [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) que devuelve la lista de encabezados para la representación. Puede agregar los encabezados utilizando la clase [MhtTemplateName](https://reference.aspose.com/email/java/com.aspose.email/mhttemplatename/). El orden en que se agregan los encabezados decide el orden en que se muestra la información.

La siguiente imagen compara las tres salidas generadas por el código de ejemplo.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

El siguiente fragmento de código demuestra el uso de la propiedad [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) para establecer el orden en que se muestra la información en los archivos MHTML de salida.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomOrderOfInformationInMHTML-1.java" >}}