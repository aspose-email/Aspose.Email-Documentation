---
title: "Diferenciar entre Anexos Inline e Anexos Regulares"
url: /pt/java/differentiate-between-inline-and-regular-attachments/
weight: 10
type: docs
---

{{% alert color="primary" %}} 

As mensagens de email podem conter imagens inline, bem como anexos. Usando [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), os anexos inline podem ser extraídos da coleção [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection), enquanto os anexos regulares podem ser acessados e extraídos com a coleção [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) de uma mensagem. No entanto, isso é diferente quando a mensagem é carregada usando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), já que todas as imagens inline e os anexos regulares são acessíveis ao usuário na mesma [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Portanto, é necessário um método que possa diferenciar entre um anexo inline e um anexo regular quando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) é usado.

{{% /alert %}} 

Este artigo explica como diferenciar anexos inline de anexos regulares usando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). Ao decidir, o tipo de corpo de [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) é levado em consideração da seguinte forma:

- **Corpo de texto simples**: Mensagens de email com tipo de corpo de texto simples não precisam ser verificadas, pois todos os anexos nessas mensagens são sempre anexos regulares.
- **Corpo HTML**: Para mensagens com um corpo HTML, o anexo não deve apenas conter a propriedade PR_ATTACH_FLAGS (0x37140003), mas seu valor deve ser igual a 0x00000004 para anexos inline. Se essa condição for atendida, então depende ainda das tags PR_ATTACH_CONTENT_LOCATION e PR_ATTACH_CONTENT_ID para determinar a natureza do anexo. No entanto, na ausência da tag MAPI PR_ATTACH_FLAGS, o anexo é verificado quanto à propriedade PR_ATTACH_DISPOSITION (0x3716001F ou 0x3716001E) para determinar o tipo de anexo.
- **Corpo RTF**: Se o corpo for RTF, então todos os anexos OLE são anexos inline. O valor de PR_ATTACH_METHOD para todos os anexos OLE é igual a 0x00000006.

O seguinte exemplo de código demonstra como diferenciar programaticamente entre anexos inline e regulares. A função isInlineAttachment recebe um anexo e MapiMessage como parâmetros de entrada e retorna true se o anexo for um anexo inline.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // ignorar indicações para mensagens de texto simples
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // verificar a propriedade PidTagAttachFlags
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // verificar a propriedade PidTagAttachContentId
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // verificar a propriedade PidTagAttachContentLocation
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
        // Se o corpo for RTF, então todos os anexos OLE são anexos inline.
        // Anexos OLE têm 0x00000006 para o valor da propriedade PidTagAttachMethod
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~



Este trecho de código usa a função isInlineAttachment() para avaliar anexos.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " é um anexo inline");
    } else {
        System.out.println(attachment.getLongFileName() + " é um anexo regular");
    }
}
~~~