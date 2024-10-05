---
title: Отображение информации в пользовательском порядке в MHTML файлах
type: docs
weight: 80
url: /java/display-information-in-custom-order-in-mhtml-files/
---

Aspose.Email предоставляет свойство [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) которое возвращает список заголовков для рендеринга. Вы можете добавить заголовки, используя класс [MhtTemplateName](https://reference.aspose.com/email/java/com.aspose.email/mhttemplatename/). Порядок, в котором добавляются заголовки, определяет порядок отображения информации.

Следующее изображение сравнивает три вывода, сгенерированных примером кода.

![todo:image_alt_text](display-information-in-custom-order-in-mhtml-files_1.jpg)

Следующий фрагмент кода демонстрирует использование свойства [MhtSaveOptions.RenderingHeaders](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/#getRenderingHeaders--) для установки порядка, в котором информация отображается в выходных MHTML файлах.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomOrderOfInformationInMHTML-1.java" >}}