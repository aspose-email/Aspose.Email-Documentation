---
title: "Converter OLM para PST"
url: /pt/net/converter-olm-para-pst/
weight: 120
type: docs
---

[OLM](https://docs.fileformat.com/email/olm/) é um formato de arquivo de banco de dados usado pelo Microsoft Outlook para sistemas Mac. Os arquivos OLM armazenam mensagens de e-mail, dados de calendário, dados de contatos e configurações de aplicativo. Um arquivo OLM não é suportado pelo Outlook para Windows. Portanto, não é possível abrir um arquivo do Outlook para Mac (OLM) no Outlook para Windows. Se você deseja migrar sua caixa de entrada do Outlook para Mac para o Outlook para Windows, é necessário converter o arquivo OLM do Outlook para Mac para o formato de arquivo PST do Outlook.

## **Etapas para converter um arquivo OLM para PST**

Para converter um arquivo OLM para PST, siga as etapas abaixo:

1. Crie uma instância da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) para abrir a OLM de origem.
2. Abra um arquivo OLM de origem.
3. Crie um novo arquivo PST usando o método [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Crie um método GetContainerClass para mapear a classe da mensagem para uma classe de pasta.
5. Crie um método AddToPst que lê recursivamente cada pasta e suas mensagens da OLM usando o método EnumerateMapiMessages e as adiciona ao PST na mesma ordem usando os métodos AddSubFolder e AddMessage.

## **Exemplo de código**

O seguinte exemplo de código mostra como converter um OLM para um PST.

**Método** Main:

```cs
// criar uma instância da classe OlmStorage para abrir a OLM de origem
using (var olm = new OlmStorage("my.olm"))
// criar um novo arquivo PST
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    // lê recursivamente cada pasta e suas mensagens
    // e as adiciona ao PST na mesma ordem
    foreach (var olmFolder in olm.FolderHierarchy)
    {
        AddToPst(pst.RootFolder, olmFolder);
    }
} 
```

**Implementação do método** GetContainerClass:

```cs
public string GetContainerClass(string messageClass)
{
    if (messageClass.StartsWith("IPM.Contact") || messageClass.StartsWith("IPM.DistList"))
    {
        return "IPF.Contact";
    }

    if (messageClass.StartsWith("IPM.StickyNote"))
    {
        return "IPF.StickyNote";
    }

    if (messageClass.StartsWith("IPM.Activity"))
    {
        return "IPF.Journal";
    }

    if (messageClass.StartsWith("IPM.Task"))
    {
        return "IPF.Task";
    }

    if (messageClass.StartsWith("IPM.Appointment") || messageClass.StartsWith("IPM.Schedule.meeting"))
    {
        return "IPF.Appointment";
    }

    return "IPF.Note";
}
```

**Implementação do método** AddToPst:

```cs
public void AddToPst(FolderInfo pstFolder, OlmFolder olmFolder)
{
    FolderInfo pstSubFolder = pstFolder.GetSubFolder(olmFolder.Name);

    foreach (var msg in olmFolder.EnumerateMapiMessages())
    {
        if (pstSubFolder == null)
        {
            pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name, GetContainerClass(msg.MessageClass));
        }

        pstSubFolder.AddMessage(msg);
    }

    if (pstSubFolder == null)
    {

        pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name);
    }

    foreach (var olmSubFolder in olmFolder.SubFolders)
    {
        AddToPst(pstSubFolder, olmSubFolder);
    }
}
```