---
title: "Отображение информации в пользовательском порядке в MHTML файлах"
url: /ru/net/display-information-in-custom-order-in-mhtml-files/
weight: 80
type: docs
---

Aspose.Email предоставляет свойство [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/), которое возвращает список заголовков для отображения. Вы можете добавить заголовки, используя класс [MhtTemplateName](https://reference.aspose.com/email/net/aspose.email/mhttemplatename/). Порядок, в котором добавляются заголовки, определяет порядок, в котором отображается информация.

Следующее изображение сравнивает три вывода, сгенерированные примером кода.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

Следующий фрагмент кода демонстрирует использование свойства [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/net/aspose.email/headersformattingoptions/renderingheaders/) для установки порядка, в котором информация отображается в выходных MHTML файлах.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomOrderOfInformationInMHTML-1.cs" >}}