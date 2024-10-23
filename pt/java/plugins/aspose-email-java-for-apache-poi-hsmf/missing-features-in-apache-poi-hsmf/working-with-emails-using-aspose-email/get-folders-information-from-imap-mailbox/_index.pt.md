---
title: "Obter Informações de Pastas da Caixa de Correio IMAP"
url: /pt/java/get-folders-information-from-imap-mailbox/
weight: 10
type: docs
---

## **Aspose.Email - Obter Informações de Pastas da Caixa de Correio IMAP**
Obter informações sobre pastas de um servidor IMAP é muito fácil com Aspose.Email. O método listFolders() do ImapClient retorna um objeto da ImapFolderInfoCollection que contém informações sobre todas as pastas do servidor. Percorra essa coleção e obtenha informações sobre pastas individuais em um loop. O método é sobrecarregado. Você pode passar um nome de pasta como um parâmetro para obter uma lista de subpastas.

**Java**

``` java

 ImapClient client = new ImapClient();

client.setHost("--server--"); //imap.secureserver.net,

client.setPort(993);

client.setUsername("--username--");

client.setPassword("--password--");

client.setSecurityOptions(SecurityOptions.Auto);

ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Percorra a coleção para obter informações da pasta uma por uma

for (ImapFolderInfo folderInfo:folderInfoColl)

{

	// Nome da pasta

	System.out.println("O nome da pasta é: " + folderInfo.getName());

	ImapFolderInfo folderExtInfo = client.listFolder(folderInfo.getName());

	// Novas mensagens na pasta

	System.out.println("Contagem de novas mensagens: " + folderExtInfo.getNewMessageCount());

	// Verifica se é somente leitura

	System.out.println("É somente leitura? " + folderExtInfo.getReadOnly());

	// Número total de mensagens

	System.out.println("Número total de mensagens: " + folderExtInfo.getTotalMessageCount());

}

```
## **Baixar Código em Execução**
Baixe **Obter Informações de Pastas da Caixa de Correio IMAP** de qualquer um dos sites de codificação social mencionados abaixo:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)