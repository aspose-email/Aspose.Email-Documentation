---
title: "Различие между встроенными и обычными вложениями"
url: /ru/java/differentiate-between-inline-and-regular-attachments/
weight: 10
type: docs
---

{{% alert color="primary" %}}

Электронные сообщения могут содержать встроенные изображения, а также вложения. Используя [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), встроенные вложения могут быть извлечены из коллекции [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection), в то время как обычные вложения могут быть доступны и извлечены с помощью коллекции [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) сообщения. Однако это отличается, когда сообщение загружается с использованием [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), так как все встроенные изображения и обычные вложения доступны пользователю в одной и той же коллекции [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Следовательно, необходим метод, который может различать встроенное и обычное вложение при использовании [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage).

{{% /alert %}}

В этой статье объясняется, как различать встроенные вложения от обычных с использованием [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). При принятии решения учитывается тип содержимого [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) следующим образом:

- **Текстовое содержимое**: Электронные сообщения с текстовым содержимым не требуют проверки, так как все вложения в таких сообщениях всегда являются обычными вложениями.
- **HTML-содержимое**: Для сообщений с HTML-содержимым, вложение должно содержать не только свойство PR_ATTACH_FLAGS (0x37140003), но и его значение должно быть равно 0x00000004 для встроенных вложений. Если это условие выполнено, то далее это зависит от тегов PR_ATTACH_CONTENT_LOCATION и PR_ATTACH_CONTENT_ID для определения характера вложения. Однако при отсутствии тега MAPI PR_ATTACH_FLAGS, вложение проверяется на наличие свойства PR_ATTACH_DISPOSITION (0x3716001F или 0x3716001E) для определения типа вложения.
- **RTF-содержимое**: Если содержимое является RTF, то все OLE-вложения являются встроенными вложениями. Значение PR_ATTACH_METHOD для всех OLE-вложений равно 0x00000006.

Следующий пример кода демонстрирует, как программно различать встроенные и обычные вложения. Функция isInlineAttachment принимает вложение и MapiMessage в качестве входных параметров и возвращает true, если вложение является встроенным.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // игнорировать указания для сообщений с обычным текстом
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // проверка свойства PidTagAttachFlags
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // проверка свойства PidTagAttachContentId
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // проверка свойства PidTagAttachContentLocation
                if (att.getProperties().containsKey(0x3713001E) 
                        || att.getProperties().containsKey(0x3713001F)) {
                    String contentLocation = att.getProperties().containsKey(0x3713001E) 
                            ? att.getPropertyString(0x3713001E) : att.getPropertyString(0x3713001F);
                    if (!contentLocation.isEmpty() && msg.getBodyHtml().contains(contentLocation)) {
                        return true;
                    }
                }
            } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                    || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
                return true;
            }
        } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
            return true;
        }
        return false;
    } else if (msg.getBodyType() == BodyContentType.Rtf) {
        // Если содержимое является RTF, то все OLE-вложения являются встроенными вложениями.
        // OLE-вложения имеют 0x00000006 для значения свойства PidTagAttachMethod
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~

Этот фрагмент кода использует функцию isInlineAttachment() для оценки вложений.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " является встроенным вложением");
    } else {
        System.out.println(attachment.getLongFileName() + " является обычным вложением");
    }
}
~~~