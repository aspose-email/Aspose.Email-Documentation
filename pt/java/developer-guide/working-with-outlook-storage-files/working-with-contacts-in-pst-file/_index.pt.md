---
title: "Trabalhando com Contatos em Arquivo PST"
url: /pt/java/trabalhando-com-contatos-em-arquivo-pst/
weight: 40
type: docs
---

## **Lendo Múltiplos Contatos em Formato VCard**

O trecho de código abaixo demonstra como ler um arquivo VCF, verificar se ele contém múltiplos contatos e, se sim, carregar os contatos do arquivo em uma lista de objetos VCardContact. O código utiliza os seguintes métodos:

- [isMultiContacts(InputStream stream)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#isMultiContacts-java.io.InputStream-) - Verifica se o fluxo de origem contém vários contatos.
- [loadAsMultiple(String filePath, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.lang.String-java.nio.charset.Charset-) - Carrega a lista de contatos de um arquivo de múltiplos contatos.
- [loadAsMultiple(InputStream stream, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.io.InputStream-java.nio.charset.Charset-) - Carrega a lista de contatos de um fluxo de múltiplos contatos.

```java
try (InputStream stream = new FileInputStream("test.vcf")) {
    if (VCardContact.isMultiContacts(stream)) {
        List<VCardContact> contacts = VCardContact.loadAsMultiple(stream, Charset.forName("utf-8"));
    }
}
```

## **Adicionando Contato ao PST**

[Criar Novo PST, Adicionar Subpastas e Mensagens](java/create-new-pst-add-sub-folders-and-messages/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar um [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) à subpasta Contatos de um arquivo PST que você criou ou carregou. Abaixo estão as etapas para adicionar um [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) a um PST:

1. Crie um objeto [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Defina as propriedades do [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) usando diferentes construtores e métodos.
1. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
1. Crie uma pasta pré-definida (Contatos) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

O trecho de código abaixo mostra como criar um [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) e, em seguida, adicioná-lo à pasta Contatos de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}

## **Salvar informações de contatos do arquivo PST no formato MSG**

Este artigo mostra como acessar informações de contato de um arquivo PST do Microsoft Outlook e salvar contatos no disco no formato MSG. Para fazer isso, use as classes [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) e [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para obter e exibir as informações de contato.

Para obter as informações de um contato:

1. Carregue o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) e, em seguida, o método [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMapiMessageItem--) para obter as informações de contato na classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Use as propriedades do [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para acessar as informações de contato.
1. Chame o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obter as informações de contato na classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
1. Chame o método [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para salvar o contato no disco no formato MSG.

Abaixo está um exemplo de código que recupera todas as informações de contatos do arquivo PST e as salva no disco no formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}

## **Salvar Informações de Contatos do PST do Outlook no Disco em formato vCard**

Este artigo mostra como acessar informações de contato de um arquivo PST do Microsoft Outlook e salvar o contato no disco em formato vCard (VCF). Ele usa as classes [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para obter as informações de contato.

Abaixo estão as etapas para obter as informações de contatos:

1. Carregue o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obter as informações de contato na classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Use as propriedades da classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) para acessar as informações de contato.

O programa abaixo carrega um arquivo PST do disco e salva todos os contatos em formato vCard (VCF). Os arquivos VCF podem ser usados em qualquer outro programa que possa carregar o arquivo de contato padrão vCard. Se você abrir qualquer arquivo VCF no Microsoft Outlook, ele se parecerá com o da captura de tela abaixo.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
| :- |
|**Figura: Um vCard salvo com Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}