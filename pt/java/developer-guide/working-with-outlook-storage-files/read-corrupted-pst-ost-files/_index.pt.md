---
title: "Ler arquivos PST/OST corrompidos"
url: /pt/java/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

## **Ler arquivos PST/OST corrompidos**

Às vezes, pode não ser possível ler o PST/OST devido a alguns problemas. Por exemplo, alguns blocos de dados podem estar corrompidos. Em tais casos, exceções geralmente surgem ao chamar os métodos [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--), etc. Mas mensagens ou pastas individuais podem permanecer intactas no armazenamento.

Os usuários do Aspose.Email podem encontrar identificadores de itens de forma hierárquica. Além disso, você pode extrair itens pelos identificadores. Para esse propósito, a biblioteca oferece os seguintes métodos:

- [PersonalStorage.findMessages(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - encontra os identificadores de mensagens para a pasta.
- [PersonalStorage.findSubfolders(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - encontra os identificadores de subpastas para a pasta.

**Nota** que, apesar das vantagens, existem armazenamentos corrompidos que não podem ser lidos mesmo usando esses métodos.

O seguinte trecho de código demonstra o uso desses métodos para ler arquivos PST/OST corrompidos:

```java
try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    exploreCorruptedPst(pst, pst.getRootFolder().getEntryIdString());
}

public static void exploreCorruptedPst(PersonalStorage pst, String rootFolderId) {
    Iterable<String> messageIdList = pst.findMessages(rootFolderId);

    for (String messageId : messageIdList) {
        try {
            MapiMessage msg = pst.extractMessage(messageId);
            System.out.println("- " + msg.getSubject());
        } catch (Exception e) {
            System.out.println("Erro ao ler a mensagem. ID de entrada: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Erro ao ler a mensagem. ID de entrada: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Extrair itens PST de arquivos corrompidos**

A API de travessia permite extrair todos os itens PST, na medida do possível, sem lançar exceções, mesmo que alguns dados do arquivo original estejam corrompidos.

Use o construtor [PersonalStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) e o método [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) em vez do método [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-).

O construtor permite definir um método de callback.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Código de tratamento de exceção. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Exceções de carregamento e travessia estarão disponíveis através do método de callback.

O método load retorna 'true' se o arquivo foi carregado com sucesso e uma nova travessia é possível. Se um arquivo estiver corrompido e nenhuma travessia for possível, 'false' é retornado.

```java
if (currentPst.load(inputStream))
```
O seguinte exemplo de código mostra como implementar a API de travessia de arquivos PST em um projeto:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Código de tratamento de exceção. */
        }
    };

    try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) {
        if (pst.load("test.pst")) {
            getAllMessages(pst, pst.getRootFolder());
        }
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