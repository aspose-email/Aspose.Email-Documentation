---
title: "Exibir informações em ordem personalizada em arquivos MHTML"
url: /pt/java/display-information-in-custom-order-in-mhtml-files/
weight: 80
type: docs
---

Aspose.Email fornece a propriedade [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) que retorna a lista de cabeçalhos para renderização. Você pode adicionar os cabeçalhos usando a classe [MhtTemplateName](https://reference.aspose.com/email/java/com.aspose.email/mhttemplatename/). A ordem em que os cabeçalhos são adicionados determina a ordem em que as informações são exibidas.

A imagem a seguir compara as três saídas geradas pelo código de exemplo.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

O seguinte trecho de código demonstra o uso da propriedade [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) para definir a ordem em que as informações são exibidas nos arquivos MHTML de saída.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomOrderOfInformationInMHTML-1.java" >}}