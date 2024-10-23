---
title: "Trabalhando com Anexos de Mensagem"
url: /pt/java/trabalhando-com-anexos-de-mensagem/
weight: 70
type: docs
---

## **Analisando e Salvando Anexos**

Os arquivos de mensagem do Outlook podem conter um ou mais anexos. O Aspose.Email permite que os desenvolvedores percorram os anexos em um arquivo MSG e os salvem no disco. Este tópico descreve o processo. Também descreve como incorporar um anexo.

A classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) do Aspose.Email é usada para carregar um arquivo MSG do disco e expõe o método [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) que faz referência à coleção de objetos [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) associada ao arquivo MSG. O objeto [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) ainda expõe métodos que executam ações sobre o anexo.

Para salvar anexos em um arquivo MSG no disco com o nome e a extensão originais:

1. Crie uma instância da classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) para carregar um arquivo MSG usando o método estático [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Chame o método [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) da classe [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) para obter uma referência à coleção de objetos [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) associados ao arquivo MSG.
3. Percorra a [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) para exibir informações sobre cada objeto [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) através de seus métodos públicos.
4. Chame o método [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) da classe [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) para salvar o anexo no disco.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Incorporando Mensagens como Anexos

Uma mensagem do Microsoft Outlook pode conter outras mensagens do Microsoft Outlook em anexos, seja como mensagens regulares, descritas acima, ou mensagens incorporadas. A [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) fornece membros sobrecarregados do método add para criar mensagens do Outlook com ambos os tipos de anexos. Arquivos MSG do Outlook incorporados em um arquivo MSG contêm um PR_ATTACH_METHOD com o valor 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Lendo uma Mensagem Incorporada de um Anexo**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Inserção e Substituição de Anexos MSG**

A API Aspose.Email fornece a capacidade de inserir anexos em um índice específico na mensagem pai. Ela também fornece a possibilidade de substituir o conteúdo de um anexo por outro anexo de mensagem.

### **Inserir Anexo MSG em Localização Específica**

A API Aspose.Email fornece a capacidade de inserir um anexo MSG em um MSG pai usando o método [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-).

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Substituir Conteúdos de Anexo MSG Incorporado**

Isso pode ser usado para substituir conteúdos de anexo incorporado pelos novos usando o método [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-). No entanto, não pode ser usado para inserir um anexo com PR_ATTACH_NUM = 4 (por exemplo) na coleção com collection.Count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Salvar Anexos de Mensagem Digitalmente Assinada**

A API Aspose.Email fornece a capacidade de obter ou definir um valor indicando se uma mensagem assinada de forma clara será decodificada.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Renomear um Anexo em um MapiMessage**

O Aspose.Email torna possível editar o valor da propriedade [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) nos [anexos MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

O seguinte exemplo de código demonstra como atualizar os nomes de exibição dos primeiros e segundos anexos dentro da mensagem Mapi carregada:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("Novo nome de exibição 1");
msg.getAttachments().get_Item(1).setDisplayName("Novo nome de exibição 2");
```
## **Verificar se um Anexo é Inline ou Regular**

A diferença entre anexos inline e regulares é como eles são apresentados dentro de um e-mail. Anexos inline são incorporados dentro do corpo do e-mail e podem ser visualizados sem precisar abrir um arquivo separado ou baixar qualquer coisa. Anexos regulares, por outro lado, são arquivos separados que estão anexados ao e-mail, mas não são exibidos diretamente dentro do corpo da mensagem e precisam ser baixados e abertos externamente. A propriedade [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) da classe [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) obtém um valor indicando se o anexo é inline ou regular.

O seguinte exemplo de código carrega uma mensagem de e-mail de um arquivo e depois recupera informações sobre os anexos, imprimindo especificamente o nome de exibição de cada anexo e se ele está inline dentro da mensagem ou não:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```