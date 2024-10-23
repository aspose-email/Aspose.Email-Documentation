---
title: "Trabalhando com Pastas no Servidor IMAP"
url: /pt/python-net/trabalhando-com-pastas-no-servidor-imap/
weight: 50
type: docs
---


## **Obtendo Informações sobre Pastas**
Obter informações sobre pastas de um servidor IMAP é muito fácil com Aspose.Email. Chame o método ListFolders() do namespace Aspose.Email.Imap. Ele retorna um objeto do tipo [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection). Percorra esta coleção e obtenha informações sobre pastas individuais em um loop. O método está sobrecarregado. Você pode passar um nome de pasta como parâmetro para obter uma lista de subpastas. O seguinte trecho de código mostra como obter informações sobre pastas de um servidor IMAP usando Aspose.Email com o método descrito nas informações.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Excluindo e Renomeando Pastas**

Os seguintes métodos da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) relacionados à gestão de pastas em um servidor de e-mail usando IMAP podem ser facilmente implementados em seu projeto com Aspose.Email:

- método delete_folder - remove permanentemente a pasta e todas as mensagens contidas nela.
- método rename_folder - altera o nome da pasta sem alterar o conteúdo dentro dela.

O trecho de código abaixo mostra como excluir ou renomear pastas no servidor IMAP programaticamente:

```py
# Excluir uma pasta e Renomear uma pasta
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Adicionando uma Nova Mensagem em uma Pasta**
Você pode adicionar uma nova mensagem à pasta usando as classes MailMessage e ImapClient. Primeiro, crie um objeto MailMessage fornecendo os valores de assunto, para e de. Em seguida, inscreva-se em uma pasta e adicione a mensagem a ela. O seguinte trecho de código mostra como adicionar uma nova Mensagem em uma pasta.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Estabelecendo MultiConexão ao Executar Operações em Lote**

Aspose.Email torna possível configurar o cliente para estabelecer múltiplas conexões simultâneas com o servidor IMAP. Isso não necessariamente aumenta o desempenho, mas é uma solução confiável para operações concorrentes. Isso é particularmente útil se o cliente precisar executar várias tarefas ao mesmo tempo, como buscar diferentes pastas de e-mail, sincronizar grandes quantidades de dados ou processar várias mensagens simultaneamente.

O trecho de código abaixo mostra como estabelecer várias conexões com o servidor IMAP enquanto faz o upload de uma coleção de mensagens de e-mail usando o método 'append_messages' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```

## **Mover Mensagens para Outra Pasta de Caixa de Correio**
Aspose.Email para .NET permite mover mensagens de uma pasta de caixa de correio para outra usando a API ImapClient. O método MoveMessage usa o id único da mensagem e o nome da pasta de destino para mover uma mensagem para a pasta de destino. O seguinte trecho de código mostra como mover mensagens para outra pasta de caixa de correio.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}
## **Copiar Mensagens para Outra Pasta de Caixa de Correio**
A API Aspose.Email fornece a capacidade de copiar mensagens de uma pasta de caixa de correio para outra. Permite copiar uma única mensagem, bem como várias mensagens usando os métodos CopyMessage e CopyMessages. O método CopyMessages oferece a capacidade de copiar várias mensagens da pasta de origem de uma caixa de correio para a pasta de destino da caixa de correio. O seguinte trecho de código mostra como copiar mensagens para outra pasta de caixa de correio.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Trabalhando com Pastas de Caixa de Correio de Uso Especial**

As caixas de correio de uso especial são pastas pré-designadas dentro de um sistema de e-mail usadas para tipos específicos de mensagens, como Enviadas, Rascunhos, Lixo, Lixeira e Arquivo. A biblioteca Aspose.Email permite o acesso a essas caixas de correio, atribuindo atributos associados a seus papéis e propósitos ao cliente. Os clientes, então, podem descobrir e apresentar automaticamente essas pastas de acordo com a necessidade, sem intervenção do usuário.

O seguinte trecho de código mostra como consultar informações sobre as caixas de correio especiais importantes (entrada, rascunho, lixo, enviado e lixeira) usando as propriedades da classe [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class), e imprimir essas informações:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```