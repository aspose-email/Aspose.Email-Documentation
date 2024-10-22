---
title: "Trabalhando com Arquivo In-Place"
url: /pt/net/trabalhando-com-arquivo-in-place/
weight: 150
type: docs
---


## **Arquivos In-Place no Office 365**

Arquivos In-Place no Office 365 fornecem aos usuários espaço adicional de armazenamento. Depois que as caixas de correio de arquivamento são ativadas, os usuários podem acessar e armazenar mensagens em sua Caixa de Correio de Arquivo usando o Microsoft Outlook e o Outlook na Web. Quando a caixa de correio com arquivamento In-Place habilitado é aberta com o Outlook, a caixa de correio de arquivamento é exibida como uma caixa de correio separada.

## **Mover Itens para o Arquivo In-Place**

A API Aspose.Email pode ser usada para mover itens para a caixa de correio de arquivo dos usuários usando o [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) método. O [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) método fornece quatro sobrecargas que estão listadas abaixo.

- [`ArchiveItem(string sourceFolderUri, Appointment appointment)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [`ArchiveItem(string sourceFolderUri, ExchangeTask task)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [`ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [`ArchiveItem(string sourceFolderUri, string uniqueId)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)

O exemplo de código dado abaixo demonstra o uso do [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) método para mover um email para a Caixa de Correio de Arquivo usando o UniqueUri.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}