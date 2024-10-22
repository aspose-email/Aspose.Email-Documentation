---
title: "Trabalhando com Propriedades MAPI"
url: /pt/java/trabalhando-com-propriedades-mapi/
weight: 60
type: docs
---

## **Definindo e Acessando Propriedades MAPI do Outlook**

Aspose.Email para Java fornece a [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) classe que representa uma propriedade MAPI:

- Nome: o nome da propriedade.
- Tag: a tag da propriedade.
- Dados: os dados da propriedade.

Este tópico também discute como definir e acessar propriedades MAPI de um arquivo de Mensagem do Outlook (MSG) usando Aspose.Email para Java. Além disso, um código de exemplo foi fornecido sobre como remover propriedades de MSGs e Anexos.

### **Ler Propriedades**

Para ler dados das propriedades MAPI de um arquivo MSG:

1. Crie uma instância da [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) classe para carregar um arquivo MSG usando o [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) método estático.
2. Defina uma referência ao método [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) do objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) para obter a [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Obtenha o objeto [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) da [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) pelas chaves [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/).
4. Obtenha os dados da propriedade usando o método apropriado getXXX() .
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Definir Propriedades Adicionais**

O seguinte código de exemplo pode ser usado para definir propriedades adicionais de uma [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) do Outlook.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Remover Propriedades**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Lendo Propriedades Mapi Nomeadas de Mensagens de Email**

Microsoft Outlook suporta a adição de propriedades MAPI nomeadas a um arquivo MSG. Essas propriedades são adicionadas pelo usuário. Desenvolvedores podem adicionar uma propriedade nomeada, por exemplo “MyProp”, a um arquivo MSG usando Aspose.Email.

Este artigo ilustra a coleção [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) para ler propriedades MAPI nomeadas de um arquivo MSG.

### **Ler Propriedade MAPI Nomeada**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Ler Propriedade Mapi Nomeada de Anexo**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}