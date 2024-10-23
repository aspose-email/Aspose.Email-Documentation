---
title: "Ler arquivo OLM do Outlook para Mac e obter informações sobre pastas e subpastas"
url: /pt/java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 130
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email para Java permite que você leia arquivos OLM do Outlook para Mac. Você pode carregar um arquivo OLM do disco em uma instância da classe [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens.

{{% /alert %}} 

## **Abrir arquivos no formato OLM**

Os arquivos no formato OLM podem ser abertos de duas maneiras:

- usando construtor
- usando o método estático FromFile

Existem diferenças no comportamento entre esses métodos. Veja a seção abaixo.

### **Abrir arquivos pelo construtor**

Para abrir um arquivo, chame o construtor da classe [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) e passe o nome completo do arquivo ou fluxo como argumento:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Abrir arquivos usando o método estático FromFile**

Para abrir um arquivo, use o método estático [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) e passe o nome completo do arquivo como argumento:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```
### **Abrir arquivos usando o método estático FromStream**

Para abrir um arquivo usando o método estático [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), passe um nome de fluxo como argumento:


## **Ler arquivo OLM**

O seguinte trecho de código mostra como carregar o arquivo OLM e obter seu conteúdo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Obter pastas**

Para recuperar pastas de um arquivo OLM (Outlook para Mac), carregue-o primeiro com a classe [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) e, em seguida, use um dos seguintes métodos, dependendo de suas necessidades:

- [getFolder(String name, boolean ignoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Obtém a pasta pelo nome.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Obtém a hierarquia de pastas/coleção de pastas.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Obtém a hierarquia de pastas.

O exemplo de código abaixo mostrará como obter uma pasta de um arquivo OLM:

```java
// Obter a pasta pelo nome
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
Ao usar o método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) para abrir um arquivo OLM, o [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) retornará null. Nesse caso, chame o método [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) explicitamente para recuperar a lista de diretórios no arquivo OLM.


### **Obter caminho da pasta**

Você também pode obter o caminho das pastas no arquivo OLM. Aspose.Email fornece a propriedade [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) que retorna o caminho da pasta. O seguinte trecho de código demonstra o uso da propriedade [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) para obter os caminhos das pastas no arquivo OLM.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Contar o número de itens na pasta**

Você também pode contar o número de itens na pasta. Aspose.Email fornece a propriedade [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) que retorna o número de itens na pasta. O seguinte trecho de código demonstra o uso da propriedade [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) para obter o número de itens nas pastas do arquivo OLM.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Enumerar mensagens de uma determinada pasta**

Aspose.Email fornece a API para trabalhar com armazenamentos OLM e extrair mensagens de uma pasta específica. As classes [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) e [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) representam informações breves sobre uma pasta e uma mensagem no armazenamento, respectivamente. A classe [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) fornece os seguintes métodos:

- **OlmFolder.getSubFolder**(String subfolderName, boolean ignoreCase) - Obtém a subpasta pelo nome.

- **OlmFolder.enumerateMapiMessages()** - Expõe o enumerador que suporta a iteração de MapiMessages na pasta atual.

- **OlmFolder.enumerateMessages()** - Expõe o enumerador que suporta a iteração de OlmMessageInfo's na pasta atual.

- **OlmFolder.enumerateMessages**(int startIndex, int count) - Expõe o enumerador que suporta a iteração de OlmMessageInfo's dentro de um intervalo dado.

- **OlmFolder.enumerateMessages**(MailQuery query) - Expõe o enumerador que suporta a iteração de OlmMessageInfo's por critérios de pesquisa.

Os exemplos de código abaixo demonstrarão o uso desses métodos:

```java
 // Enumera todas as mensagens em uma pasta determinada

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumera um intervalo de mensagens em uma pasta determinada

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   int startIndex = 10;

   int count = 100;

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(startIndex, count)) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumera mensagens por critérios de pesquisa

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

    MailQueryBuilder mailQueryBuilder = new MailQueryBuilder();

    mailQueryBuilder.getSubject().contains("invitation");

    mailQueryBuilder.getFrom().contains("Mark");

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(mailQueryBuilder.getQuery())) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumera todas as mensagens e a extração de algumas delas

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

       if (messageInfo.hasAttachments()) {

            MapiMessage msg = olm.extractMapiMessage(messageInfo);

       }

   }

} finally {

    olm.dispose();

}
```
## **Extrair mensagens de OLM por identificadores**

Às vezes, é necessário extrair mensagens selecionadas por identificadores. Por exemplo, seu aplicativo armazena identificadores em um banco de dados e extrai uma mensagem sob demanda. Esta é a forma eficiente de evitar percorrer todo o armazenamento a cada vez para encontrar uma mensagem específica a ser extraída. Para implementar esse recurso para arquivos OLM, Aspose.Email fornece os seguintes métodos e classes:

- a propriedade [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) da classe [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) - Obtém o identificador da entrada da mensagem.
- método sobrecarregado [extractMapiMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) da classe [OlmStorage]() - Obtém a mensagem do OLM.

O exemplo de código abaixo demonstra como extrair mensagens de OLM por identificadores:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Nota:** O ID da mensagem é único dentro do arquivo de armazenamento. Os IDs são criados pelo Aspose.Email e não podem ser usados em outras libs ou aplicativos de processamento de OLM de terceiros.


## **Extrair itens OLM de arquivos corrompidos**

Aspose.Email fornece uma API de percurso que permite extrair todos os itens OLM na medida do possível, sem lançar exceções, mesmo que alguns dados do arquivo original estejam corrompidos.

Use o construtor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) e o método [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) em vez do método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-).

O construtor permite definir um método de callback.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de tratamento de exceção. */
    }
});
```
As exceções de carga e percurso estarão disponíveis através do método de callback.

O método load retorna 'true' se o arquivo foi carregado com sucesso e é possível um percurso adicional. Se um arquivo estiver corrompido e nenhum percurso for possível, 'false' é retornado.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de tratamento de exceção. */
    }
};
try (OlmStorage olm = new OlmStorage(exceptionsCallback)) {
    if (olm.load(fileName)) {
        List<OlmFolder> folderHierarchy = olm.getFolders();
        extractItems(olm, folderHierarchy);
    }
}

private static void extractItems(OlmStorage olm, List<OlmFolder> folders) {
    for (OlmFolder folder : folders) {
        if (folder.hasMessages()) {
            System.out.println(folder);

            for (MapiMessage msg : olm.enumerateMessages(folder)) {
                System.out.println(msg.getSubject());
            }
        }

        if (folder.getSubFolders().size() > 0) {
            extractItems(olm, folder.getSubFolders());
        }
    }
}
```
## **Obter data de modificação da mensagem**

A propriedade [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) permite que você obtenha a data de modificação da mensagem.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```