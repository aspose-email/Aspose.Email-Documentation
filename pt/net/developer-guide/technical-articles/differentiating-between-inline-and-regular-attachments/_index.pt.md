---
title: "Diferenciando entre Anexos Inline e Regulares"
url: /pt/net/differentiating-between-inline-and-regular-attachments/
weight: 200
type: docs
---


É um cenário comum quando uma mensagem de email pode conter imagens inline dentro de seu corpo, bem como anexos regulares associados a ela. Usando a classe [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage), os anexos inline podem ser extraídos da classe [LinkedResourceCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/linkedresources), enquanto os anexos regulares podem ser acessados/extrados com a classe [AttachmentCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/attachments) de uma mensagem. No entanto, isso é diferente quando a mensagem é carregada usando a classe Aspose.Email.Mapi.MapiMessage, pois todas as imagens inline e anexos regulares são acessíveis ao usuário na mesma classe MapiAttachmentCollection. Portanto, é necessário desenvolver um método que possa diferenciar entre um anexo inline e um anexo regular quando o MapiMessage é utilizado.
## **Usando Aspose.Email para Diferenciar entre Anexos Inline e Regulares**
Este artigo explica como diferenciar anexos inline de anexos regulares usando o MapiMessage. Para determinar essa diferenciação, o tipo de corpo do MapiMessage é considerado da seguinte forma:

**Corpo de Texto Simples:** Mensagens de email com tipo de corpo de texto simples não precisam ser verificadas, pois todos os anexos nessas mensagens são sempre anexos regulares.

**Corpo HTML:** No caso de uma mensagem com tipo de corpo HTML, o anexo não deve apenas conter a propriedade PR_ATTACH_FLAGS (0x37140003), mas também seu valor deve ser igual a 0x00000004 para anexos inline. Se essa condição for atendida, então depende ainda das Tags PR_ATTACH_CONTENT_LOCATION e PR_ATTACH_CONTENT_ID para determinar a natureza do anexo. No entanto, na ausência da tag Mapi PR_ATTACH_FLAGS, o anexo é verificado quanto à propriedade PR_ATTACH_DISPOSITION (0x3716001F ou 0x3716001E) para determinar o tipo de anexo.

**Corpo Rtf:** Se o corpo for RTF, então todos os anexos OLE são anexos inline. O valor de PR_ATTACH_METHOD para todos os anexos OLE é igual a 0x00000006.

O seguinte exemplo de código demonstra como diferenciar programaticamente entre anexos inline e regulares. A função IsInlineAttachment leva um anexo e o tipo de corpo da mensagem como parâmetros de entrada e retorna verdadeiro se o anexo for um anexo inline.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-IdentifyInlineAndRegularAttachments-IdentifyInlineAndRegularAttachments.cs" >}}