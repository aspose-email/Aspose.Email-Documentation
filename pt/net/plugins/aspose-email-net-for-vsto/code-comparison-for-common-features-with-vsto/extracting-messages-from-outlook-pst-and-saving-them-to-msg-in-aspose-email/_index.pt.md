---
title: "Extraindo Mensagens do PST do Outlook e Salvando-as em MSG no Aspose.Email"
url: /pt/net/extracting-messages-from-outlook-pst-and-saving-them-to-msg-in-aspose-email/
weight: 130
type: docs
---

## **VSTO**
``` cs

 string pstFilePath = "sample.pst";

Outlook.Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");
// Adicione o arquivo PST (Arquivo de Dados do Outlook) ao Perfil Padrão
outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["sample"].GetRootFolder();

// Percorra todas as pastas no arquivo PST

// TODO: Isso não é recursivo

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

	Items items = folder.Items;

	foreach (object item in items)

	{

		if (item is MailItem)

		{

			// Recupere o Objeto em MailItem

			MailItem mailItem = item as MailItem;

			Console.WriteLine("Salvando mensagem {0} ....", mailItem.Subject);

			// Salve a mensagem no disco em formato MSG

			// TODO: O nome do arquivo pode conter caracteres inválidos [\ / : * ? " < > |]

			mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg", OlSaveAsType.olMSG);

		}

	}

}

// Remova o arquivo PST do Perfil Padrão

outlookNs.RemoveStore(rootFolder);

```
## **Aspose.Email**
``` cs

 string pstFilePath ="sample.pst";

// Crie uma instância de PersonalStorage e carregue o PST do arquivo

using (PersonalStorage personalStorage = PersonalStorage.FromFile(pstFilePath))

{

	// Obtenha a lista de subpastas no arquivo PST

	FolderInfoCollection folderInfoCollection = personalStorage.RootFolder.GetSubFolders();

	// Percorra todas as pastas no arquivo PST

	// TODO: Isso não é recursivo

	foreach (FolderInfo folderInfo in folderInfoCollection)

	{

		// Obtenha todas as mensagens nesta pasta

		MessageInfoCollection messageInfoCollection = folderInfo.GetContents();

		// Percorra todas as mensagens nesta pasta

		foreach (MessageInfo messageInfo in messageInfoCollection)

		{

			// Extraia a mensagem na instância MapiMessage

			MapiMessage message = personalStorage.ExtractMessage(messageInfo);

			Console.WriteLine("Salvando mensagem {0} ....", message.Subject);

			// Salve a mensagem no disco em formato MSG

			// TODO: O nome do arquivo pode conter caracteres inválidos [\ / : * ? " < > |]

			message.Save(@"\extracted\" + message.Subject + ".msg");

		}

```
## **Baixar Código Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772941)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Extract.Messages.from.PST.file.n.Save.in.MSG.Format.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip)