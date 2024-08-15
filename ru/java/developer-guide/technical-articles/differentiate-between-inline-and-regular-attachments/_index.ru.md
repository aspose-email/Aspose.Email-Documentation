---
title: "Различайте встроенные и обычные вложения"
url: /ru/java/differentiate-between-inline-and-regular-attachments/
weight: 10
type: docs
---

{{% alert color="primary" %}}

Сообщения электронной почты могут содержать встроенные изображения и вложения. Использование [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), встроенные вложения можно извлечь из [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection) коллекция, в то время как к обычным вложениям можно получить доступ и извлечь их вместе с сообщением [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) коллекция. Однако дело обстоит иначе, когда сообщение загружается с помощью [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), поскольку все встроенные изображения и обычные вложения доступны пользователю в одном и том же [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Таким образом, это метод, позволяющий отличить встроенное и обычное вложение, когда [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) используется по необходимости.

{{% /alert %}}

В этой статье объясняется, как отличить встроенные вложения от обычных, используя [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). При принятии решения учитывается тип телосложения [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) учитывается следующим образом:

- **Текст в виде обычного текста**: Сообщения электронной почты с текстовым типом текста проверять не нужно, так как все вложения в таких сообщениях всегда являются обычными вложениями.
- **Тело HTML**: Для сообщений с текстом HTML вложение должно содержать не только свойство PR_ATTACH_FLAGS (0x37140003), но и его значение должно быть равно 0x00000004 для встроенных вложений. Если это условие выполнено, то определение характера вложения также зависит от тегов PR_ATTACH_CONTENT_LOCATION и PR_ATTACH_CONTENT_ID. Однако при отсутствии тега PR_ATTACH_FLAGS MAPI вложение проверяется на наличие свойства PR_ATTACH_DISPOSITION (0x3716001F или 0x3716001E) для определения типа вложения.
- **Корпус RTF**: Если корпус выполнен в формате RTF, то все вложения OLE являются встроенными вложениями. Значение PR_ATTACH_METHOD для всех вложений OLE равно 0x00000006.

В следующем примере кода показано, как программно различать встроенные и обычные вложения. Функция isInlineAttachment принимает вложение и MAPIMessage в качестве входных параметров и возвращает значение true, если вложение является встроенным вложением.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // ignore indications for plain text messages
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // check the PidTagAttachFlags property
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // check PidTagAttachContentId property
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // check PidTagAttachContentLocation property
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
        // If the body is RTF, then all OLE attachments are inline attachments.
        // OLE attachments have 0x00000006 for the value of the PidTagAttachMethod property
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~



В этом фрагменте кода используется функция isInlineAttachment () для оценки вложений.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " is inline attachment");
    } else {
        System.out.println(attachment.getLongFileName() + " is regular attachment");
    }
}
~~~
