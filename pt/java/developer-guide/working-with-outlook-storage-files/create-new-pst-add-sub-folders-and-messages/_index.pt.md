---
title: "Criar Novo PST, Adicionar Subpastas e Mensagens"
url: /pt/java/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---

Além de analisar um arquivo PST existente, o Aspose.Email oferece meios para criar um arquivo PST do zero. Este artigo demonstra como criar um arquivo PST do Outlook e adicionar uma subpasta a ele.

1. [Criando um novo arquivo PST](#creating-a-new-pst-file-and-add-subfolders).
2. [Alterando a classe do contêiner de uma pasta](#changing-a-folders-container-class).
3. [Adicionar Mensagens em Lote com Desempenho Aprimorado](#add-bulk-messages-with-improved-performance) 

Utilize a classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) para criar um arquivo PST em algum local em um disco local. Para criar um arquivo PST do zero:

1. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
2. Adicione uma subpasta na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-).

O seguinte trecho de código mostra como criar um arquivo PST e adicionar uma subpasta chamada Caixa de Entrada.

```java
// Criar novo PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Adicionar nova pasta "Teste"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Criar PST com Tamanho maior que 2Gb usando OutputStream**

Os usuários do Aspose.Email podem otimizar o cache interno do PST usando o construtor PersonalStorage:

- **blockSize** - O tamanho de bloco ideal para expandir o buffer de cache (em bytes).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Reduzir o tamanho da mensagem e o tamanho do arquivo PST criado**

O Aspose.Email oferece a capacidade de compactar o conteúdo do corpo, o que pode ajudar a reduzir o tamanho da mensagem. Isso pode ser particularmente útil ao enviar mensagens grandes ou ao lidar com restrições de largura de banda ou armazenamento. Para esse fim, a biblioteca fornece o parâmetro de compressão incluído nos seguintes métodos:

- [MapiMessageItemBase.setBodyContent(String content, /*BodyContentType*/int contentType, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Define o conteúdo do corpo.
- [MapiMessageItemBase.setBodyRtf(String content, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Obtém ou define o texto da mensagem formatado em RTF.

O trecho de código abaixo demonstra como usar a Compactação RTF ao definir o corpo da mensagem MAPI:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// definir o corpo em html e mantê-lo comprimido
// isso reduzirá o tamanho da mensagem
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Criar PersonalStorage baseado em SeekableByteChannel Stream**

O Aspose.Email para Java torna possível trabalhar com arquivos de Armazenamento Pessoal (PST) usando java.nio.channels. Ele permite que você crie uma instância de PersonalStorage usando um fluxo SeekableByteChannel. O seguinte trecho de código demonstra como criar uma instância de PersonalStorage baseada em um fluxo FileChannel, adicionar uma subpasta chamada "messageFolder" à pasta raiz, e importar mensagens de arquivos no diretório "messageFolder": 

```cs
try (RandomAccessFile raf = new RandomAccessFile("test.pst", "rw")) {
    FileChannel channel = raf.getChannel();
    try (PersonalStorage pst = PersonalStorage.create(channel, FileFormatVersion.Unicode)) {
        FolderInfo messageFolder = pst.getRootFolder().addSubFolder("messageFolder");

        for (File f : new File("messageFolder").listFiles()) {
            messageFolder.addMessage(MapiMessage.load(f.getAbsolutePath()));
        }
    }
}
```

## **Alterando a Classe do Contêiner de uma Pasta**

Às vezes, é necessário mudar a classe de uma pasta. Um exemplo comum é onde mensagens de diferentes tipos (compromissos, mensagens, etc.) são adicionadas à mesma pasta. Em tais casos, a classe da pasta precisa ser alterada para que todos os elementos na pasta sejam exibidos corretamente. O seguinte trecho de código mostra como alterar a classe do contêiner de uma pasta em PST para esse propósito.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Adicionar Mensagens em Lote com Desempenho Aprimorado**

Adicionar mensagens individuais a um PST implica mais operações de I/O em disco e pode desacelerar o desempenho. Para um desempenho aprimorado, mensagens podem ser adicionadas ao PST em modo de lote para minimizar as operações de I/O. 
O método [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) permite que você adicione mensagens em lote e pode ser usado nos seguintes cenários. Além disso, o evento [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) ocorre quando uma mensagem é adicionada à pasta.

### **Adicionar Mensagens de Outro PST**

Para adicionar mensagens de outro PST, use o método [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) que retorna `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Obter a pasta pelo nome
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Trata o evento MessageAdded.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Adicionado: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### **Adicionar Mensagens do Diretório**

Para adicionar mensagens de um diretório, crie o método `getMessages(String pathToDir)` que retorna `Iterable<MapiMessage>`:

```java
// Ler mensagens do diretório.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Trata o evento MessageAdded.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Adicionado: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```