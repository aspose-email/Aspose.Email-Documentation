---
title: "Extraindo Mensagens do Outlook PST e Salvando-as em MSG"
url: /pt/java/extracting-messages-from-outlook-pst-and-saving-them-to-msg/
weight: 60
type: docs
---


{{% alert color="primary" %}} 

Esta dica de migração mostra como extrair mensagens de um arquivo PST do Outlook e salvá-las no disco como arquivos MSG. Envolve várias etapas:

1. Ler o arquivo PST do Outlook,
1. extrair mensagens e, finalmente,
1. salvar as mensagens extraídas.

Existem diferentes maneiras de alcançar o mesmo resultado: este artigo compara o uso do VSTO e do Aspose.Email. Primeiro, temos [exemplos de código para usar Microsoft Office Interop](#using-microsoft-office-interop) para extrair mensagens do PST. Depois desse exemplo, [exemplos de código mostram como usar Aspose.Email Outlook](#using-asposeemail), em Java, para realizar a mesma tarefa.

{{% /alert %}} 
## **Usando Microsoft Office Interop**
Para usar objetos de Automação do Office para Microsoft Outlook, adicione referências às bibliotecas Microsoft Office Interop para Outlook ao projeto. O Microsoft Office Outlook também deve estar instalado na máquina onde o código é executado. O namespace usado no exemplo de código a seguir é Microsoft.Office.Interop.Outlook.
### **Exemplos de Programação**
**C#**

~~~cs

 string pstFilePath = @"C:\sample.pst";

Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Adicionar arquivo PST (Arquivo de Dados do Outlook) ao Perfil Padrão

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["items"].GetRootFolder();

// Percorrer todas as pastas no arquivo PST

// TODO: Isso não é recursivo

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

    Items items = folder.Items;

    foreach (object item in items)

    {

        if (item is MailItem)

        {

            // Recuperar o Objeto em MailItem

            MailItem mailItem = item as MailItem;

            Console.WriteLine("Salvando mensagem {0} ....", mailItem.Subject);

            // Salvar a mensagem no disco em formato MSG

            // TODO: O nome do arquivo pode conter caracteres inválidos [\ / : * ? " < > |]

            mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg",OlSaveAsType.olMSG);

        }

    }

}

// Remover arquivo PST do Perfil Padrão

outlookNs.RemoveStore(rootFolder);

~~~
## **Usando Aspose.Email**
Os trechos de código a seguir fazem a mesma coisa que [o código acima](#using-microsoft-office-interop) mas usam Aspose.Email. Com o Aspose.Email para Java instalado, o Microsoft Outlook não é mais necessário na máquina. Basta referenciar o Aspose.Email para compilar e executar o projeto com sucesso.
### **Amostras de Programação**

~~~Java

String pstFilePath = "C:\\sample.pst";

// Criar uma instância de PersonalStorage e carregar o PST do arquivo
try (PersonalStorage personalStorage = PersonalStorage.fromFile(pstFilePath)) {
    // Obter a lista de subpastas no arquivo PST
    FolderInfoCollection folderInfoCollection = personalStorage.getRootFolder().getSubFolders();

    // Percorrer todas as pastas no arquivo PST
    // Isso não é recursivo
    for (FolderInfo folderInfo : folderInfoCollection) {
        // Obter todas as mensagens nesta pasta
        MessageInfoCollection messageInfoCollection = folderInfo.getContents();

        // Loop por todas as mensagens nesta pasta
        for (MessageInfo messageInfo : messageInfoCollection) {
            // Extrair a mensagem na instância MapiMessage
            MapiMessage message = personalStorage.extractMessage(messageInfo);

            System.out.println("Salvando mensagem " + message.getSubject() + " ...");

            // Salvar a mensagem no disco em formato MSG
            // TODO: O nome do arquivo pode conter caracteres inválidos [\ / : * ? " < > |]
            message.save("\\extracted\\" + message.getSubject() + ".msg");
        }
    }
}

~~~