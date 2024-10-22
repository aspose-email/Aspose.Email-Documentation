---
title: "Mostrar información en orden personalizado en archivos MHTML"
url: /es/net/display-information-in-custom-order-in-mhtml-files/
weight: 80
type: docs
---


Aspose.Email proporciona la propiedad [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/) que devuelve la lista de encabezados para renderizar. Puedes agregar los encabezados usando la clase [MhtTemplateName](https://reference.aspose.com/email/net/aspose.email/mhttemplatename/). El orden en el que se agregan los encabezados decide el orden en el que se muestra la información.

La siguiente imagen compara las tres salidas generadas por el código de ejemplo.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

El siguiente fragmento de código demuestra el uso de la propiedad [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/) para establecer el orden en el que se muestra la información en los archivos MHTML de salida.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomOrderOfInformationInMHTML-1.cs" >}}