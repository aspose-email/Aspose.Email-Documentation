---
title: "Trabalhando com Mensagens de Servidor IMAP"
url: /pt/python-net/trabalhando-com-mensagens-de-servidor-imap/
weight: 70
type: docs
---


## **Obtendo as Informações de Identificação para Mensagens Recebidas de uma Caixa de Correio**

Ao recuperar e processar mensagens de email, você pode buscar os detalhes das mensagens usando seus números de sequência. 

Os seguintes recursos são usados para interagir com uma caixa de correio IMAP:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) classe - Representa informações de identificação sobre uma mensagem em uma caixa de correio.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propriedade - O número de sequência de uma mensagem.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propriedade - O id único de uma mensagem.


O trecho de código abaixo mostra como obter informações de identificação sobre mensagens:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

msg_infos = client.list_messages("INBOX")

for msg_info in msg_infos:
    # fetch by sequence number
    msg = client.fetch_message(msg_info.sequence_number)

    # fetch by unique id
    msg = client.fetch_message(msg_info.unique_id)
```


## **Listando IDs de Mensagens MIME do Servidor**
ImapMessageInfo fornece o MIME MessageId para a identificação de mensagens sem extrair a mensagem completa. O seguinte trecho de código mostra como listar o MIME messageId.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Listando Mensagens do Servidor**

O método 'list_messages' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) busca uma lista de todas as mensagens da pasta atualmente selecionada (a "Caixa de Entrada" neste caso). Esta lista contém objetos de metadados de mensagem, que normalmente incluem informações como IDs de mensagem, números de sequência, UIDs e possivelmente dados resumidos, como linhas de assunto ou informações do remetente.

O trecho de código abaixo demonstra como recuperar os metadados das mensagens da Caixa de Entrada e imprimir o número total de mensagens que ela contém: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total de Mensagens: {len(messages)}")
```

## **Listando Mensagens do Servidor Recursivamente**
O protocolo IMAP suporta a listagem de mensagens recursivamente a partir de uma pasta de caixa de correio. Isso ajuda a listar mensagens de subpastas de uma pasta também. O seguinte trecho de código mostra como listar mensagens recursivamente.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Listando Mensagens com MultiConexão**

A classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) fornece uma propriedade 'use_multi_connection' para usar várias conexões em operações de alta carga. Você também pode definir o número de conexões em modo de multiconexão usando a propriedade 'connections_quantity'. O trecho de código abaixo demonstra o uso do modo de multiconexão na listagem de mensagens:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Observe que usar este modo não necessariamente leva a um aumento de desempenho.*

## **Obter Mensagens em Ordem Descendente**

A tarefa é realizada definindo configurações de paginação para a recuperação de mensagens. Para isso, use a propriedade 'ascending_sorting' da classe [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class), que faz parte do módulo do cliente IMAP. Defina o atributo 'ascending_sorting' no objeto PageSettings como False. Isso indica que as mensagens devem ser ordenadas em ordem descendente por padrão durante a recuperação. O seguinte trecho de código mostra como recuperar mensagens em ordem descendente:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

page_settings = ae.clients.imap.PageSettings
page_settings.ascending_sorting = False
page_info = client.list_messages_by_page(5, page_settings)
messages = page_info.items

for message in messages:
    print(message.subject)
```

## **Buscar Mensagens do Servidor e Salvar no Disco**
A classe ImapClient pode buscar mensagens de um servidor IMAP e salvar as mensagens em formato EML em um disco local. Os seguintes passos são necessários para salvar as mensagens no disco:

1. Crie uma instância da classe ImapClient.
1. Especifique o nome do host, nome de usuário e senha no construtor do ImapClient.
1. Selecione a pasta usando o método SelectFolder().
1. Chame o método ListMessages para obter o objeto ImapMessageInfoCollection.
1. Itere pela coleção ImapMessageInfoCollection, chame o método SaveMessage() e forneça o caminho de saída e o nome do arquivo.

O seguinte trecho de código mostra como buscar mensagens de email de um servidor e salvá-las.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}
## **Salvar Mensagens em Formato MSG**
No exemplo acima, os emails são salvos em formato EML. Para salvar emails em formato MSG, o método ImapClient.FetchMessage() precisa ser chamado. Ele retorna a mensagem em uma instância da classe MailMessage. O método MailMessage.Save() pode então ser chamado para salvar a mensagem em MSG. O seguinte trecho de código mostra como salvar mensagens em formato MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Buscar Mensagens por Número de Sequência ou ID Único**

A biblioteca permite que você gere duas listas de mensagens, uma contendo os números de sequência e outra contendo os IDs únicos de todas as mensagens na caixa de entrada. Para buscar mensagens do servidor IMAP por esses identificadores, use o método 'fetch_messages' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class). O trecho de código abaixo demonstra como listar mensagens por identificadores:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Listar mensagens
message_info_col = client.list_messages()
print("Contagem de ListMessages:", message_info_col.count)

# Obter números de sequência e IDs únicos
sequence_number_ar = [mi.sequence_number for mi in message_info_col]
unique_id_ar = [mi.unique_id for mi in message_info_col]

# Buscar mensagens por número de sequência
fetched_messages_by_snum = client.fetch_messages(sequence_number_ar)
print("FetchMessages-sequenceNumberAr Count:", len(fetched_messages_by_snum))

# Buscar mensagens por UID
fetched_messages_by_uid = client.fetch_messages(unique_id_ar)
print("FetchMessages-uniqueIdAr Count:", len(fetched_messages_by_uid))
```

## **Listando Mensagens com Suporte a Paginação**
Em cenários onde o servidor de email contém um grande número de mensagens na caixa de correio, muitas vezes é desejável listar ou recuperar as mensagens com suporte a paginação. O ImapClient da API Aspose.Email permite que você recupere as mensagens do servidor com suporte a paginação.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Listando Anexos de Mensagens**

Para obter informações sobre anexos, como nome e tamanho, sem buscar os dados do anexo, use os seguintes recursos da biblioteca:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) classe - Representa informações de anexo (tamanho, nome, tipo de mídia).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) classe - Representa a coleção de [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class).

- '`list_attachments(sequence_number)`' método da classe [`ImapClient`](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) - Obtém um iterável ou coleção de informações de anexos para a mensagem.

```py
# Listar mensagens
message_info_col = client.list_messages()

# Iterar por cada mensagem
for message_info in message_info_col:
    print(f"Anexos para a mensagem com número de sequência {message_info.sequence_number}:")

    # Listar anexos para a mensagem atual
    attachment_info_col = client.list_attachments(message_info.sequence_number)

    # Iterar por cada anexo
    for attachment_info in attachment_info_col:
        print(f"Anexo: {attachment_info.name} (tamanho: {attachment_info.size})")
```
## **Obtendo Pastas e Lendo Mensagens Recursivamente**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) usa o método recursivo para listar pastas e subpastas do servidor IMAP. O mesmo método também é usado para ler e salvar mensagens no disco local em formato MSG. Pastas e mensagens são criadas e salvas na mesma estrutura hierárquica que no servidor IMAP. O seguinte trecho de código mostra como obter pastas e mensagens recursivamente:

```py
import aspose.email as ae
import os

# Método recursivo para obter mensagens de pastas e subpastas
def list_messages_in_folder(folder_info, root_folder, client):
    # Criar a pasta no disco (mesmo nome que no servidor IMAP)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Ler as mensagens da pasta atual, se for selecionável
    if folder_info.selectable:
        # Enviar um comando de status para obter informações da pasta
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"Pasta {folder_info_status.name} selecionada. Novas mensagens: {folder_info_status.new_message_count}, "
            f"Total de mensagens: {folder_info_status.total_message_count}"
        )

        # Selecionar a pasta atual e listar mensagens
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Listando mensagens....")
        for msg_info in msg_info_coll:
            # Obter o assunto e outras propriedades da mensagem
            print("Assunto:", msg_info.subject)
            print(
                f"Lida: {msg_info.is_read}, Recente: {msg_info.recent}, Respondida: {msg_info.answered}"
            )

            # Remover caracteres como ? e :, que não devem ser incluídos em um nome de arquivo
            # Salvar a mensagem em formato MSG
            file_name = (
                msg_info.subject.replace(":", " ").replace("?", " ")
                + "-"
                + str(msg_info.sequence_number)
                + ".msg"
            )
            msg = client.fetch_message(msg_info.sequence_number)
            msg.save(
                os.path.join(current_folder, file_name),
                ae.SaveOptions.default_msg_unicode,
            )
        print("============================\n")
    else:
        print(f"{folder_info.name} não é selecionável.")

    try:
        # Se esta pasta tiver subpastas, chame este método recursivamente para obter mensagens
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass



client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # A pasta raiz (que será criada no disco) consiste no host e no nome de usuário
    root_folder = f"{client.host}-{client.username}"

    # Criar a pasta raiz e listar todas as pastas do servidor IMAP
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Chame o método recursivo para ler mensagens e obter subpastas
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nMensagens baixadas recursivamente do servidor IMAP.")
```


## **Recuperando Parâmetros Extras como Informações Resumidas**


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Obtendo Informações do Cabeçalho List-Unsubscribe**

O cabeçalho "ListUnsubscribe" é comumente incluído nos cabeçalhos de mensagens de email enviadas por listas de discussão ou sistemas de email automatizados. Ele fornece um link ou endereço de email que os destinatários podem usar para cancelar a inscrição da lista de discussão ou dos emails automatizados. Aspose.Email fornece a propriedade 'list_unsubscribe' da classe [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) para recuperar esse cabeçalho. O trecho de código abaixo demonstra o uso da propriedade e pode ser usado como parte de um sistema para automatizar o processo de cancelamento de inscrição de emails indesejados:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterar por cada mensagem
for imap_message_info in message_info_col:
    print("Cabeçalho ListUnsubscribe:", imap_message_info.list_unsubscribe)
```