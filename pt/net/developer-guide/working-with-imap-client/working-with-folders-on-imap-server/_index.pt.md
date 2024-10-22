---
title: "Trabalhando com Pastas no Servidor IMAP"
url: /pt/net/trabalhando-com-pastas-no-servidor-imap/
weight: 60
type: docs
---


## **Obtendo Informações sobre Pastas**

Obter informações sobre pastas de um servidor IMAP é muito fácil com Aspose.Email. Chame o [método ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Ele retorna um objeto do tipo [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/). Percorra essa coleção e obtenha informações sobre pastas individuais em um loop. O método está sobrecarregado. Você pode passar um nome de pasta como parâmetro para obter uma lista de subpastas. O seguinte trecho de código mostra como obter informações de pastas de um servidor IMAP usando Aspose.Email com o método descrito na informação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Excluindo e Renomeando Pastas**

Uma pasta em um servidor IMAP pode ser excluída ou renomeada em uma única linha com Aspose.Email:

- O método [`DeleteFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) aceita o nome da pasta como um parâmetro.
- Para o método [`RenameFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/), você precisa passar o nome atual da pasta e o novo nome da pasta.

O seguinte trecho de código mostra como remover uma pasta de um servidor IMAP e como renomear uma pasta. Cada operação é realizada com uma linha de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Adicionando uma Nova Mensagem em uma Pasta**

Você pode adicionar uma nova mensagem à pasta usando as classes [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Primeiro, crie um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) fornecendo o assunto, valores de para e de. Depois, inscreva-se em uma pasta e adicione a mensagem a ela. O seguinte trecho de código mostra como adicionar uma nova mensagem em uma pasta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Adicionar Várias Mensagens com Suporte a MultiConexão**

Você pode adicionar várias mensagens usando o método [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) fornecido pelas classes [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). O método [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) aceita uma lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e a adiciona à pasta atual se a pasta não for fornecida como um parâmetro. O ImapClient também oferece suporte ao modo MultiConexão para operações com carga pesada. O seguinte trecho de código mostra como adicionar várias mensagens usando o modo MultiConexão.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Por favor, observe que o uso do modo multiconexão não garante aumento de desempenho.

{{% /alert %}} 

## **Mover Mensagens para Outra Pasta de Caixa de Entrada**

Aspose.Email para .NET permite mover mensagens de uma pasta de caixa de entrada para outra usando a API [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). O método [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) utiliza o id único da mensagem e o nome da pasta de destino para mover uma mensagem para a pasta de destino. O seguinte trecho de código mostra como mover mensagens para outra pasta de caixa de entrada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Copiar Mensagens para Outra Pasta de Caixa de Entrada**

A API Aspose.Email fornece a capacidade de copiar mensagens de uma pasta de caixa de entrada para outra. Ela permite copiar uma única mensagem, bem como várias mensagens, usando os métodos [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) e [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/). O método [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) oferece a capacidade de copiar várias mensagens da pasta de origem de uma caixa de entrada para a pasta de destino. O seguinte trecho de código mostra como copiar mensagens para outra pasta de caixa de entrada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Trabalhando com Pastas de Caixa de Entrada de Uso Especial**

Alguns armazenamentos de mensagens IMAP incluem caixas de entrada de uso especial, como aquelas usadas para manter mensagens de rascunho ou mensagens enviadas. Muitos clientes de e-mail permitem que os usuários especifiquem onde as mensagens de rascunho ou enviadas devem ser colocadas, mas configurá-las requer que o usuário saiba quais caixas de entrada o servidor reservou para esses fins. Aspose.Email pode identificar essas caixas de entrada de uso especial usando a classe [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) para facilitar o trabalho com elas. O seguinte exemplo de código demonstra como acessar essas caixas de entrada de uso especial usando a classe [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}