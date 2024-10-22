---
title: "Trabalhando com Pastas no Exchange Server"
url: /pt/net/trabalhando-com-pastas-no-exchange-server/
weight: 80
type: docs
---


## **Listando todas as Pastas do Servidor**

A API Aspose.Email fornece a capacidade de se conectar ao Exchange Server e listar todas as pastas e subpastas. Você também pode recuperar todas as subpastas de cada pasta recursivamente. Ela também fornece a capacidade de enumerar pastas com paginação a partir do cliente Exchange usando o Exchange Web Service (EWS). Este artigo mostra como recuperar todas as subpastas do servidor Exchange e como recuperar pastas com paginação.

O seguinte trecho de código mostra como listar pastas do Exchange Server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}

## **Obter Informações sobre o Tipo de Pasta usando EWS**

A propriedade [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/foldertype/) fornecida pela classe [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/) pode ser usada para obter informações sobre o tipo da pasta. Isso é mostrado no exemplo de código abaixo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}

## **Enumerando Pastas com Suporte a Paginação usando EWS**

O seguinte trecho de código mostra como usar o suporte a paginação usando EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}

## **Acessando Pastas Personalizadas ou Subpastas da Caixa de Correio**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) permite que os desenvolvedores acessem qualquer pasta personalizada ou subpasta da caixa de correio. A função [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) da classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) retorna o URI de uma pasta/subpasta personalizada especificada, que pode ser usada para acessar a pasta desejada. No exemplo a seguir, uma pasta personalizada chamada "TestInbox", que é criada sob a INBOX, é acessada e todas as mensagens são exibidas dessa pasta personalizada. Para realizar essa tarefa, siga os seguintes passos:

1. Inicialize o objeto [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) fornecendo credenciais válidas.
1. Acesse a caixa de correio padrão.
1. Acesse a pasta pai, que é a INBOX neste exemplo. Essa pasta pai também pode ser uma pasta personalizada.
1. Use [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/folderexists/#folderexists/) para pesquisar a subpasta personalizada especificada, por exemplo "TestInbox". Ele retornará o URI de "TestInbox".
1. Use este URI para acessar todas as mensagens nessa pasta personalizada.

O seguinte trecho de código mostra como acessar pastas personalizadas ou subpastas da caixa de correio com EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}

## **Listando Pastas Públicas**

O Microsoft Exchange Server permite que os usuários criem pastas públicas e publiquem mensagens nelas. Para fazer isso através de seu aplicativo, use a classe Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para se conectar ao Exchange Server e ler e baixar mensagens e postagens de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas e subpastas, listar e baixar quaisquer mensagens encontradas nessas pastas. Este exemplo funciona apenas com o Microsoft Exchange Server 2007 ou superior, pois apenas estes suportam EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}

## **Copiar uma Mensagem para outra Pasta**

A API Aspose.Email permite copiar uma mensagem de uma pasta para outra usando o método [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/#copyitem). A versão sobrecarregada deste método retorna o URI Único da mensagem copiada, conforme mostrado neste artigo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}

## **Sincronizando Itens de Pasta**

A interface Aspose.Email para .NET [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) proporciona a funcionalidade de sincronizar uma pasta Exchange para seu conteúdo. O método [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/syncfolder/#syncfolder/) exposto pela classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) pode ser usado para realizar a sincronização das informações da pasta em uma pasta especificada. O seguinte trecho de código mostra como sincronizar as informações da pasta do Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}

## **Recuperando Permissões para Pastas do Exchange**

Os usuários são atribuídos permissões para pastas públicas no Exchange Server, o que limita/determina o nível de acesso que um usuário possui a essas pastas. A classe [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/) fornece um conjunto de propriedades de permissão para pastas do Exchange, como o [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/permissionlevel/), se eles podem [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/cancreateitems/), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/deleteitems/) e realizar outras tarefas conforme especificado pelas propriedades de permissão. As permissões podem ser recuperadas usando o método [GetFolderPermissions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getfolderpermissions/#getfolderpermissions) da classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/). Este artigo mostra como recuperar as permissões aplicadas a uma pasta pública para todos os usuários que têm acesso às pastas compartilhadas.

Para realizar essa tarefa:

1. Inicialize o [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/ewsclient/).
1. Use o [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listpublicfolders/#listpublicfolders) para obter uma lista de todas as pastas públicas.
1. Recupere as permissões associadas a uma pasta usando o método [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/getfolderpermissions/#getfolderpermissions).

O seguinte trecho de código mostra como usar a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para recuperar permissões aplicadas a uma pasta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}

## **Criando Pastas e Subpastas**

A API Aspose.Email fornece a capacidade de criar pastas em uma caixa de correio Exchange. O método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) da classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) pode ser utilizado para esse propósito. Para criar uma pasta na caixa de correio do Exchange, os seguintes passos podem ser seguidos.

1. Crie uma instância de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Defina a propriedade [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/useslashasfolderseparator/) conforme necessário. Se definir como **true**, o aplicativo considerará a "barra" como separador de pasta e a subpasta será criada após a barra.
1. Use o método [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createfolder/#createfolder/) para criar a pasta.

O seguinte trecho de código mostra como criar pastas e subpastas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}

## **Fazer Backup das Pastas do Exchange em PST**

Frequentemente acontece que os usuários podem querer fazer um backup de todas ou algumas das pastas da caixa de correio. A Aspose.Email fornece a capacidade de fazer backup de todas ou das pastas de caixa de correio Exchange especificadas para um PST. Este artigo descreve como fazer o backup das pastas do Exchange para um PST com código de exemplo. Para fazer o backup das pastas do servidor Exchange, os seguintes passos podem ser seguidos.

1. Inicie o [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) com as credenciais do usuário.
1. Adicione as informações das pastas necessárias à [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection/).
1. Use o método [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/backup/#backup/) do cliente para exportar o conteúdo da pasta para PST.

O seguinte trecho de código mostra como fazer backup das pastas do Exchange para PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}