---
title: "Trabalhando com Listas de Distribuição"
url: /pt/python-net/trabalhando-com-listas-de-distribuicao/
weight: 40
type: docs
---

É possível criar uma lista de distribuição usando a API Aspose.Email, que é uma coleção de múltiplos contatos. Uma lista de distribuição pode ser salva em disco no formato MSG do Outlook e pode ser visualizada/manipulada ao abri-la no MS Outlook.
## **Criando e Salvando uma Lista de Distribuição**
O seguinte trecho de código mostra como criar e salvar uma lista de distribuição.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}

## **Lendo uma Lista de Distribuição de um PST**

O seguinte trecho de código mostra como ler uma lista de distribuição de um arquivo PST.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file( "your_pst_file.pst")
folder = pst.root_folder.get_sub_folder("Contacts")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    dlist = msg.to_mapi_message_item()
    if isinstance(dlist, ae.mapi.MapiDistributionList):
        for member in dlist.members:
            print("Nome de Exibição do Membro:", member.display_name)
            print("Endereço de Email do Membro:", member.email_address)
```