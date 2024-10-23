---
title: "Obtendo Lista de Mensagens da Pasta de Entrada da Caixa de Correio do Microsoft Exchange Server"
url: /pt/java/obtendo-lista-de-mensagens-da-pasta-de-entrada-da-caixa-de-correio-do-microsoft-exchange-server/
weight: 50
type: docs
---


{{% alert color="primary" %}} 

Nossas dicas de migração mostram como os produtos Aspose podem ser usados para melhorar suas aplicações e libertá-lo da dependência de automação tradicional.

Esta dica de migração conecta-se a uma caixa de correio do Microsoft Exchange Server e obtém uma lista de mensagens da pasta de Entrada. Os exemplos de código abaixo mostram como usar [Microsoft Office Interop](#using-microsoft-office-interop) para obter uma lista de mensagens antes de fazer a mesma coisa usando classes do [Aspose.Email Exchange](#using-asposeemail), usando Java.

{{% /alert %}} 
## **Usando Microsoft Office Interop**
Para usar objetos de Automação do Office para Microsoft Outlook, adicione referências às bibliotecas Microsoft Office e Microsoft Office Interop para Outlook ao projeto. O Microsoft Office Outlook também deve estar instalado na máquina onde o código é executado.
### **Exemplos de Programação**
**C#**

~~~cs

 // Criar classe Application e obter namespace

Outlook.Application outlook = new Outlook.ApplicationClass();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Obter informações da Caixa de Entrada no objeto do tipo MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// E-mails não lidos

int unread = inbox.UnReadItemCount;

// Exibir o assunto dos e-mails na pasta de Entrada
foreach (Outlook.MailItem mail in inbox.Items)

{

    Console.WriteLine(Wmail.Subject);


}


~~~
## **Usando Aspose.Email**
Os seguintes trechos de código fazem a mesma coisa que [os trechos acima](#using-microsoft-office-interop), mas usam Aspose.Email.

No entanto, o Microsoft Outlook não precisa estar instalado na máquina onde o código é executado. Referencie o Aspose.Email para compilar e executar o projeto com sucesso.
### **Exemplos de Programação**

~~~java

// Criar instância da classe IEWSClient fornecendo credenciais
try (IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", "username", "password", "domain")) {
    // Chamar o método listMessages para listar informações das mensagens da Caixa de Entrada

    ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

    // Percorrer a coleção para exibir as informações básicas
    for (ExchangeMessageInfo msgInfo : msgCollection) {
        System.out.println("Subject: " + msgInfo.getSubject());
        System.out.println("From: " + msgInfo.getFrom().toString());
        System.out.println("To: " + msgInfo.getTo().toString());
        System.out.println("Message ID: " + msgInfo.getMessageId());
        System.out.println("Unique URI: " + msgInfo.getUniqueUri());
        System.out.println("==================================");
    }
}

~~~