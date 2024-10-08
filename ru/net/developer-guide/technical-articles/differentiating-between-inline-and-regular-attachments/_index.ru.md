---
title: "Различение встроенных и обычных вложений"
url: /ru/net/differentiating-between-inline-and-regular-attachments/
weight: 200
type: docs
---

Это распространенный сценарий, когда электронное сообщение может содержать встроенные изображения в своем теле, а также обычные вложения, связанные с ним. Используя класс [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage), встроенные вложения можно извлечь из класса [LinkedResourceCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/linkedresources), тогда как обычные вложения можно получить/извлечь с помощью класса [AttachmentCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/attachments) сообщения. Однако это отличается, когда сообщение загружается с использованием класса Aspose.Email.Mapi.MapiMessage, так как все встроенные изображения и обычные вложения доступны пользователю в одном и том же классе MapiAttachmentCollection. Следовательно, необходимо разработать метод, который сможет различать встроенные и обычные вложения, когда используется MapiMessage.
## **Использование Aspose.Email для различения встроенных и обычных вложений**
Эта статья объясняет, как различать встроенные вложения от обычных с использованием MapiMessage. Чтобы определить это различие, учитывается тип тела MapiMessage следующим образом:

**Тело в простом тексте:**  Электронные сообщения с телом в простом тексте не нужно проверять, так как все вложения в таких сообщениях всегда являются обычными вложениями.

**Html Тело:** В случае сообщения с телом HTML, вложение должно не только содержать свойство PR_ATTACH_FLAGS (0x37140003), но также его значение должно быть равно 0x00000004 для встроенных вложений. Если это условие выполнено, то все зависит от тегов PR_ATTACH_CONTENT_LOCATION и PR_ATTACH_CONTENT_ID для определения природы вложения. Однако при отсутствии тега Mapi PR_ATTACH_FLAGS вложение проверяется по свойству PR_ATTACH_DISPOSITION (0x3716001F или 0x3716001E), чтобы определить тип вложения.

**Rtf Тело:** Если тело является RTF, то все OLE-вложения являются встроенными вложениями. Значение PR_ATTACH_METHOD для всех OLE-вложений равно 0x00000006.

Следующий пример кода демонстрирует, как программно различать встроенные и обычные вложения. Функция IsInlineAttachment принимает вложение и тип тела сообщения в качестве входных параметров и возвращает true, если вложение является встроенным.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-IdentifyInlineAndRegularAttachments-IdentifyInlineAndRegularAttachments.cs" >}}