---
title: "Ler arquivo PST do Outlook e obter informações sobre pastas e subpastas"
url: /pt/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email para Java permite ler arquivos PST do Microsoft Outlook. Você pode carregar um arquivo PST do disco ou fluxo em uma instância da classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens.

{{% /alert %}} 

## **Carregar um arquivo PST**

Um arquivo PST do Outlook pode ser carregado em uma instância da classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/). Um exemplo de código para carregar o arquivo PST é dado abaixo:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Exibindo informações das pastas**

Após carregar o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/), você pode obter informações sobre o nome de exibição do arquivo, pasta raiz, subpastas e contagem de mensagens. O seguinte trecho de código exibe o nome de um arquivo PST, pastas e número de mensagens nas pastas:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Obter apenas pastas definidas pelo usuário**

Arquivos PST/OST podem conter pastas que foram criadas pelo usuário. Aspose.Email fornece a capacidade de acessar apenas pastas definidas pelo usuário usando a propriedade [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--). Você pode definir a propriedade [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) como **true** para obter apenas pastas definidas pelo usuário. O seguinte trecho de código demonstra o uso de [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) para obter pastas definidas pelo usuário.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Verificando se a pasta está em uma pasta pré-definida**

Ao abrir e inspecionar as pastas dentro de um arquivo PST (Tabela de Armazenamento Pessoal), você pode verificar se cada pasta é um tipo de pasta pré-definida ou uma subpasta de um tipo de pasta pré-definida e obter informações sobre cada pasta.

O método [FolderInfo.getPredefinedType(boolean getForTopLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) é usado para verificar se a pasta é do [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/). 

Se o parâmetro 'getForTopLevelParent' for verdadeiro, o método retorna um valor de enumeração StandardIpmFolder para a pasta pai de nível superior. Isso determina se a pasta atual é uma subpasta de uma pasta pré-definida. Se o parâmetro 'getForTopLevelParent' for falso, ele retorna um valor de enumeração StandardIpmFolder para a pasta atual.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Display Name: " + folder.getDisplayName());

        // Determina se a pasta atual é uma pasta pré-definida
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "Não" : "Sim, " + folderType;
        System.out.println("É uma StandardIpmFolder?: " + answer);

        // Determina se a pasta atual é uma subpasta de uma pasta pré-definida
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "Não" : "Sim, " + folderType;
            System.out.println("É subpasta de uma pasta StandardIpmFolder?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Obter ou adicionar uma pasta padrão de feeds RSS em um arquivo PST**

Aspose.Email torna possível recuperar uma referência à pasta pré-definida que contém feeds RSS. Isso pode ser útil se você desejar acessar e manipular programaticamente os feeds RSS armazenados em um arquivo PST do Outlook. Dê o valor de RssFeeds para a enumeração [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/).

O seguinte exemplo de código mostra como obter uma pasta de feeds RSS:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
E o exemplo de código abaixo demonstra como adicionar uma pasta de feeds RSS:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("Feeds RSS", StandardIpmFolder.RssFeeds);
}
```

## **Analisar pastas pesquisáveis**

Um PST/OST pode conter pastas pesquisáveis além do tipo normal de pastas. Aspose.Email fornece o enumerador [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) para especificar as mensagens de tais pastas de busca com os métodos [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) e [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Recuperar informações da pasta pai a partir de MessageInfo**

O seguinte trecho de código mostra como recuperar informações da pasta pai a partir de [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **API de travessia de arquivos PST**

A API de travessia permite extrair todos os itens PST, tanto quanto possível, sem gerar exceções, mesmo que alguns dados do arquivo original estejam corrompidos. As seguintes etapas mostram como usar esta API.

Use o construtor [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e o método [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) em vez do método fromFile.

O construtor permite definir um método de callback.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Código de tratamento de exceções.
    }
})) {
    //
}
```

Exceções de carregamento e travessia estarão disponíveis através do método de callback.

O método [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) retorna 'true' se o arquivo foi carregado com sucesso e a travessia posterior é possível. Se um arquivo estiver corrompido e nenhuma travessia for possível, 'false' é retornado.

```java
if (currentPst.load(inputStream))
```

Isso permite abrir e atravessar até arquivos PST corrompidos sem gerar exceções. Tanto as exceções quanto os itens corrompidos serão tratados pelo método de callback.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Código de tratamento de exceções.
    }
})) {
    if (pst.load("test.pst")) {
        getAllMessages(pst, pst.getRootFolder());
    }
}

private static void getAllMessages(PersonalStorage pst, FolderInfo folder) {
    for (String messageEntryId : folder.enumerateMessagesEntryId()) {
        MapiMessage message = pst.extractMessage(messageEntryId);
    }
    for (FolderInfo subFolder : folder.getSubFolders()) {
        getAllMessages(pst, subFolder);
    }
}
```