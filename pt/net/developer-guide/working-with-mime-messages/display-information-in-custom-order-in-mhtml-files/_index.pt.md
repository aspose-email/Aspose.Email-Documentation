---
title: "Exibir Informações em Ordem Personalizada em Arquivos MHTML"
url: /pt/net/display-information-in-custom-order-in-mhtml-files/
weight: 80
type: docs
---


Aspose.Email fornece a propriedade [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/) que retorna a lista de cabeçalhos para renderização. Você pode adicionar os cabeçalhos usando a classe [MhtTemplateName](https://reference.aspose.com/email/net/aspose.email/mhttemplatename/). A ordem em que os cabeçalhos são adicionados decide a ordem em que as informações são exibidas.

A imagem a seguir compara as três saídas geradas pelo código de exemplo.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

O seguinte trecho de código demonstra o uso da propriedade [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/) para definir a ordem em que as informações são exibidas nos arquivos MHTML de saída.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomOrderOfInformationInMHTML-1.cs" >}}