---
title: "Trabalhando com Listas de Distribuição"
url: /pt/net/trabalhando-com-listas-de-distribuicao-em-pst/
weight: 40
type: docs
---

É possível criar uma lista de distribuição usando a API Aspose.Email, que é uma coleção de múltiplos contatos. Uma lista de distribuição pode ser salva no disco no formato MSG do Outlook e pode ser visualizada/ manipulada ao ser aberta no MS Outlook.

### **Criando e Salvando uma Lista de Distribuição**

O seguinte trecho de código mostra como criar e salvar uma lista de distribuição.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cs" >}}

### **Lendo uma Lista de Distribuição de um PST**

O seguinte trecho de código mostra como ler uma lista de distribuição de um PST.

```cs
using Aspose.Email.Storage.Pst;
using Aspose.Email.Mapi;

// Load the PST file
using (var pst = PersonalStorage.FromFile("your.pst"))
{
    // Get the Contacts folder
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    if (folder != null)
    {
        foreach (var msgInfo in folder.EnumerateMessages())
        {
            // Check if the message has the "IPM.DistList" message class
            if (msgInfo.MessageClass == "IPM.DistList")
            {
                // Extract the distribution list
                var distList = (MapiDistributionList)pst.ExtractMessage(msgInfo).ToMapiMessageItem();
                
                // Now, you can work with the distribution list
                // (e.g., access its members, display its properties, or make modifications)
            }
        }
    }
}
```

### **Atualizando uma Lista de Distribuição em PST**

O seguinte trecho de código mostra como atualizar uma lista de distribuição em PST.

```cs
using Aspose.Email.Mapi;
using Aspose.Email.Storage.Pst;

// Load PST file
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
{
    // Get Contacts folder
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    // Add a new member to each distribution list in PST
    foreach (var msg in folder.EnumerateMessages())
    {
        // Check if the message has the "IPM.DistList" message class
        if (msg.MessageClass == "IPM.DistList")
        {
            var distList = pst.ExtractMessage(msg).ToMapiMessageItem();

            // Create a new member to add
            var member = new MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com");
            distList.Members.Add(member);

            // Update Distribution List in PST
            folder.UpdateMessage(msg.EntryIdString, distList);
        }
    }
}
```