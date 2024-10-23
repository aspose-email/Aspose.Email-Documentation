---
title: "Trabalhando com Pastas no Exchange Server"
url: /pt/cpp/trabalhando-com-pastas-no-exchange-server/
weight: 80
type: docs
---

## **Listando todas as Pastas do Servidor**
A API Aspose.Email fornece a capacidade de conectar-se ao Exchange Server e listar todas as pastas e subpastas. Você também pode recuperar todas as subpastas de cada pasta de forma recursiva. Ela também oferece a capacidade de enumerar pastas com paginação do cliente Exchange usando o Exchange Web Service (EWS). Este artigo mostra como recuperar todas as subpastas do servidor Exchange e recuperar pastas com paginação.

O seguinte trecho de código mostra como listar pastas do Exchange Server.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cpp" >}}
## **Obter Informações sobre o Tipo de Pasta usando EWS**
O enumerador [ExchangeFolderType](https://apireference.aspose.com/email/cpp/namespace/aspose.email.clients.exchange#a613cbc66cee5ccade16eca706187441f) fornecido pela classe [ExchangeFolderInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info) pode ser usado para obter informações sobre o tipo da pasta. Isso é mostrado no exemplo de código abaixo.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cpp" >}}
## **Enumerando Pastas com Suporte a Paginação usando EWS**
O seguinte trecho de código mostra como usar o suporte à paginação com EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cpp" >}}
## **Acessando Pastas Personalizadas ou Subpastas da Caixa de Correio**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite que os desenvolvedores acessem qualquer pasta personalizada ou subpasta da caixa de correio. O método [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) retorna o URI de uma pasta/sub-pasta personalizada especificada, que pode ser usada para acessar a pasta de destino. No exemplo a seguir, uma pasta personalizada chamada "TestInbox", que é criada sob a INBOX, é acessada e todas as mensagens são exibidas a partir dessa pasta personalizada. Para realizar essa tarefa, os seguintes passos são realizados:

1. Inicialize o objeto [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) fornecendo credenciais válidas.
1. Acesse a caixa de correio padrão.
1. Acesse a pasta pai, que é a INBOX neste exemplo. Esta pasta pai também pode ser uma pasta personalizada.
1. Use o método [FolderExists()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a5d15162d540bd7a8f47fbafcab88f380) para procurar a subpasta personalizada especificada, por exemplo, "TestInbox". Ele retornará o URI de "TestInbox".
1. Use esse URI para acessar todas as mensagens daquela pasta personalizada.

O seguinte trecho de código mostra como acessar pastas personalizadas ou subpastas da caixa de correio com EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-1.cpp" >}}
## **Listando Pastas Públicas**
O Microsoft Exchange Server permite que os usuários criem pastas públicas e publiquem mensagens nelas. Para fazer isso através de seu aplicativo, use a classe [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) para conectar-se ao Exchange Server e ler e baixar mensagens e postagens de pastas públicas. O seguinte trecho de código mostra como ler todas as pastas públicas e subpastas, e listar e fazer o download de quaisquer mensagens encontradas nessas pastas. Este exemplo só funciona com o Microsoft Exchange Server 2007 ou superior, já que somente esses suportam EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Sincronizando Itens de Pasta**
A API Aspose.Email do [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) fornece a funcionalidade de sincronizar uma pasta Exchange para seu conteúdo. O método [SyncFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93d8936ab504a137498c6c2fd53648b6) exposto pela classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) pode ser usado para sincronizar informações de uma pasta especificada. O seguinte trecho de código mostra como sincronizar informações da pasta de exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cpp" >}}
## **Recuperando Permissões para Pastas do Exchange**
Os usuários são atribuídos permissões a pastas públicas no Exchange Server, que limitam/determinam o nível de acesso que um usuário tem a essas pastas. A classe *ExchangeFolderPermission* fornece um conjunto de propriedades de permissão para pastas Exchange, como o *nível de permissão*, se podem criar itens, deletar itens, e realizar outras tarefas conforme especificado pelas propriedades de permissão. As permissões podem ser recuperadas usando o método [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601) da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Este artigo mostra como recuperar as permissões aplicadas a uma pasta pública para todos os usuários que têm acesso às pastas compartilhadas.

Para realizar essa tarefa:

1. Inicialize o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Use o [ListPublicFolders](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae3eb469ff721575748a90f579095e296) para obter uma lista de todas as pastas públicas.
1. Recupere as permissões associadas a uma pasta usando o método [GetFolderPermissions()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ad16ac1877140e0011686d4728a62f601).

O seguinte trecho de código mostra como usar a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para recuperar permissões aplicadas a uma pasta.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cpp" >}}
## **Criando Pastas e Sub-Pastas**
A API Aspose.Email fornece a capacidade de criar pastas em uma caixa de correio Exchange. O método [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) pode ser usado para esse fim. Para criar uma pasta na caixa de correio do servidor Exchange, os seguintes passos podem ser seguidos.

1. Crie uma instância de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Defina a propriedade [set_UseSlashAsFolderSeparator](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a47baa33ffe28fe893653f8bcc710a268) como necessário. Se definida como **true**, a aplicação considerar "Barra" como separador de pasta e a subpasta será criada após a barra.
1. Use o método [CreateFolder](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a362509196a9bae1630ed0a6fdf132159) para criar a pasta.

O seguinte trecho de código mostra como criar pastas e sub-pastas.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cpp" >}}
## **Fazendo Backup de Pastas do Exchange para PST**
Muitas vezes, os usuários podem querer fazer um backup de todas ou algumas das pastas da caixa de correio. A Aspose.Email fornece a capacidade de fazer um backup de todas ou pastas de caixa de correio Exchange especificadas para um PST. Para fazer um backup das pastas do servidor Exchange, os seguintes passos podem ser seguidos.

1. Crie uma instância de [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Adicione as informações da pasta necessária ao [ExchangeFolderInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_folder_info_collection).
1. Use o método [IEWSClient->Backup](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9f78c7e2b5de5148bd98b3dc1e0e4038) para exportar o conteúdo da pasta para PST.

O seguinte trecho de código mostra como fazer backup de pastas do Exchange para PST.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cpp" >}}