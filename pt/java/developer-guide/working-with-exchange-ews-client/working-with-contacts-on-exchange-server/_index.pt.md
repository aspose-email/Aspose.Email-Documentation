---
title: "Trabalhando com Contatos no Exchange Server"
url: /pt/java/trabalhando-com-contatos-no-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} As contas do Exchange Server contêm mais do que apenas mensagens de email. Além de [recuperar](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [mover](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [enviar](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) e [deletar mensagens de email](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) de servidores Exchange, o Aspose.Email permite trabalhar com contatos. Este artigo explica como recuperar informações de contato usando os Serviços Web do Exchange. Este artigo também mostra como você pode listar contatos da pasta de Contatos ou resolver contatos com base no nome do contato. {{% /alert %}} 
## **Obtendo Contatos com EWS**
Aspose.Email fornece a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. Os trechos de código a seguir usam os Serviços Web do Exchange para ler todos os contatos. O seguinte trecho de código mostra como obter Contatos com EWS.



~~~Java
// Criar instância da classe IEWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Listar todos os contatos
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    MapiContact mapiContact = Contact.to_MapiContact(contact);
    // Mostrar nome e endereço de email
    System.out.println("Nome: " + mapiContact.getNameInfo().getDisplayName() + "+ Endereço de Email: " + mapiContact.getElectronicAddresses().getEmail1());
}
~~~
## **Resolver Contatos usando o Nome do Contato**
O seguinte trecho de código mostra como usar para obter contatos com EWS



~~~Java
// Criar instância da classe IEWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Listar todos os contatos
Contact[] contacts = client.resolveContacts("Changed Name", ExchangeListContactsOptions.FetchPhoto);
for (Contact c : contacts) {
    MapiContact contact = Contact.to_MapiContact(c);
    // Mostrar nome e endereço de email
    System.out.println("Nome: " + contact.getNameInfo().getDisplayName() + "+ Endereço de Email: " + contact.getElectronicAddresses().getEmail1());
}
~~~
## **Determinando o Formato das Notas do Contato**
O NotesFormat especifica o tipo de formato de texto das notas dos contatos definido pelo enumerador TextFormat.

## **Buscar Contato usando o Id**
Um contato específico pode ser recuperado do servidor usando seu id de contato, como mostrado no seguinte exemplo de código.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Adicionando Contatos**
A classe [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) pode utilizar o método [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) para adicionar informações de Contato a um Exchange Server. O método [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) aceita um objeto [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) como parâmetro de entrada.

Para adicionar contatos a um Exchange Server:

1. Inicializar o EWSClient com o endereço e credenciais.
1. Inicializar o objeto Contact com as propriedades desejadas.
1. Chamar o método CreateContact para adicionar o contato ao Exchange Server.

Aspose.Email fornece a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. Os trechos de código mostram como usar os Serviços Web do Exchange para adicionar contatos a um Exchange Server.



~~~Java
// Definir mailboxURI, nome de usuário, senha, informações do domínio
String mailboxUri = "https://ex2010/ews/exchange.asmx";
String username = "test.exchange";
String password = "pwd";
String domain = "ex2010.local";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Criar Novo Contato
Contact contact = new Contact();

// Definir informações gerais
contact.setGender(Gender.Male);
contact.setDisplayName("Frank Lin");
contact.setCompanyName("ABC Co.");
contact.setJobTitle("Executive Manager");
PhoneNumber tmp0 = new PhoneNumber();
tmp0.setNumber("123456789");
tmp0.setCategory(PhoneNumberCategory.getHome());

// Adicionar números de telefone
contact.getPhoneNumbers().add(tmp0);
AssociatedPerson tmp1 = new AssociatedPerson();
tmp1.setName("Catherine");
tmp1.setCategory(AssociatedPersonCategory.getSpouse());

// pessoas associadas ao contato
contact.getAssociatedPersons().add(tmp1);
AssociatedPerson tmp2 = new AssociatedPerson();
tmp2.setName("Bob");
tmp2.setCategory(AssociatedPersonCategory.getChild());
contact.getAssociatedPersons().add(tmp2);
AssociatedPerson tmp3 = new AssociatedPerson();
tmp3.setName("Merry");
tmp3.setCategory(AssociatedPersonCategory.getSister());
contact.getAssociatedPersons().add(tmp3);
Url tmp4 = new Url();
tmp4.setHref("www.blog.com");
tmp4.setCategory(UrlCategory.getBlog());

// URLs
contact.getUrls().add(tmp4);
Url tmp5 = new Url();
tmp5.setHref("www.homepage.com");
tmp5.setCategory(UrlCategory.getHomePage());
contact.getUrls().add(tmp5);
EmailAddress tmp6 = new EmailAddress();
tmp6.setAddress("Frank.Lin@Abc.com");
tmp6.setDisplayName("Frank Lin");
tmp6.setCategory(EmailAddressCategory.getEmail1());

// Definir o endereço de Email do contato
contact.getEmailAddresses().add(tmp6);

try {
    client.createContact(contact);
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Atualizando Contatos**
As informações de contato podem ser atualizadas usando o Microsoft Outlook. O Aspose.Email também pode atualizar informações de contato no Exchange Server usando os Serviços Web do Exchange (EWS). O método [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) da classe [IEWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) pode atualizar as informações de contato no Exchange Server.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Listar todos os contatos e percorrer todos os contatos
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Nome: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Deletando Contatos**
A classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) fornece o método [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) para acessar e deletar contatos da pasta de contatos de um Exchange Server. Este método aceita o ID do contato como parâmetro de entrada.

Para deletar contatos de um Exchange Server:

1. Inicializar o ExchangeWebServiceClient com endereço e credenciais.
1. Deletar um contato usando seu ID.

Os seguintes trechos de código mostram como deletar contatos de um servidor Exchange usando o serviço web do Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String strContactToDelete = "John Teddy";
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    if (contact.getDisplayName().equals(strContactToDelete))
        client.deleteItem(contact.getId().getEWSId(), DeletionOptions.getDeletePermanently());

}
client.dispose();
~~~