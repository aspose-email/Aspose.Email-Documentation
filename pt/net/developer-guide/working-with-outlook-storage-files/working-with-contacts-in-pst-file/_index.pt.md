---
title: "Trabalhando com Contatos em Arquivo PST"
url: /pt/net/trabalhando-com-contatos-em-arquivo-pst/
weight: 40
type: docs
---


## **Adicionando Contato ao PST**

O artigo [Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostra como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar um MapiContact à subpasta Contatos de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiContact a um PST:

1. Crie um objeto [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
2. Defina as [propriedades do MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) usando diferentes construtores e métodos.
3. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crie uma pasta pré-definida (Contatos) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

O seguinte trecho de código mostra como criar um MapiContact e, em seguida, adicioná-lo à pasta de contatos de um arquivo PST recém-criado.

```csharp
// Criar três Contatos 
var contact1 = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");
var contact2 = new MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Investimento Grau A");
var contact3 = new MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Fábrica de Sofás Krauses", "046-630-4614046-630-4614");

// Contato #4
var contact4 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Margaret", "J.", "Tolle")};
contact4.PersonalInfo.Gender = MapiContactGender.Female;
contact4.ProfessionalInfo = new MapiContactProfessionalPropertySet("Adaptaz", "Engenheira de gravação");
contact4.PhysicalAddresses.WorkAddress.Address = "4 Darwinia Loop EIGHTY MILE BEACH WA 6725";
contact4.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com");
contact4.Telephones.BusinessTelephoneNumber = "(08)9080-1183";
contact4.Telephones.MobileTelephoneNumber = "(925)599-3355(925)599-3355";

// Contato #5
var contact5 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Matthew", "R.", "Wilcox")};
contact5.PersonalInfo.Gender = MapiContactGender.Male;
contact5.ProfessionalInfo = new MapiContactProfessionalPropertySet("Briazz", "Auxiliar psiquiátrico");
contact5.PhysicalAddresses.WorkAddress.Address = "Horner Strasse 12 4421 SAASS";
contact5.Telephones.BusinessTelephoneNumber = "0650 675 73 300650 675 73 30";
contact5.Telephones.HomeTelephoneNumber = "(661)387-5382(661)387-5382";

// Contato #6
var contact6 = new MapiContact
{
    NameInfo = new MapiContactNamePropertySet("Bertha", "A.", "Buell"),
    ProfessionalInfo = new MapiContactProfessionalPropertySet("Awthentikz", "Assistente de trabalho social")
};
contact6.PersonalInfo.PersonalHomePage = "B2BTies.com";
contact6.PhysicalAddresses.WorkAddress.Address = "Im Astenfeld 59 8580 EDELSCHROTT";
contact6.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com");
contact6.Telephones = new MapiContactTelephonePropertySet("06605045265");

using (PersonalStorage personalStorage = PersonalStorage.Create("SampleContacts_out.pst", FileFormatVersion.Unicode))
{
    var contactFolder = personalStorage.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    contactFolder.AddMapiMessageItem(contact1);
    contactFolder.AddMapiMessageItem(contact2);
    contactFolder.AddMapiMessageItem(contact3);
    contactFolder.AddMapiMessageItem(contact4);
    contactFolder.AddMapiMessageItem(contact5);
    contactFolder.AddMapiMessageItem(contact6);
}
```

## **Salvar informações de contatos do arquivo PST no formato MSG**

Este artigo explica como acessar informações de contato de um arquivo PST do Outlook e salvar o contato em disco no formato MSG. Os passos para obter as informações de contato são:

1. Carregue o arquivo PST no objeto [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos através de um loop pelos mensagens.
1. Verifique se o valor da propriedade [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) corresponde a "IPM.Contact".
1. Chame o método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obter o objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Chame o método MapiMessage.Save() para salvar o contato em disco no formato MSG.

O seguinte trecho de código mostra como recuperar todas as informações de contato do arquivo PST e salvar em disco no formato MSG.

```csharp
// Carregar o arquivo PST do Outlook
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Obtenha a pasta Contatos
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Loop através de todos os contatos nesta pasta
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Obter as informações de contato
        var msg = pst.ExtractMessage(messageInfo);
        
        // Salvar em disco no formato msg
        string contactName = msg.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        msg.Save($"{contactName}.msg", SaveOptions.DefaultMsgUnicode);
    }
}
```

## **Salvar informações de Contatos do arquivo PST no formato VCF**

Este artigo mostra como acessar informações de contato de um arquivo PST do Microsoft Outlook e salvar o contato em disco no formato vCard (VCF). Use as classes [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) para obter informações de contato do arquivo PST. Para obter as informações de contato:

1. Carregue o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos através de um loop pelos mensagens.
1. Verifique se o valor da propriedade [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) corresponde a "IPM.Contact".
1. Chame o método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obter o objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Chame o método [MapiMessage.ToMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomapimessageitem/) e faça o cast do [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/) para o tipo [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Chame o método [MapiContact.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_1) para salvar o contato em disco no formato VCard.

O programa abaixo carrega um arquivo PST do disco e salva todos os contatos no formato vCard (VCF). Os arquivos VCF podem ser usados em qualquer outro programa que possa carregar o arquivo de contato padrão vCard. Se você abrir qualquer arquivo VCF no Microsoft Outlook, ele terá a aparência da captura de tela abaixo.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
O seguinte trecho de código mostra como exportar contatos do PST do Outlook para o formato vCard (VCF).

```csharp
// Carregar o arquivo PST do Outlook
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Obtenha a pasta Contatos
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Loop através de todos os contatos nesta pasta
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Obter as informações de contato
        var msg = pst.ExtractMessage(messageInfo);
        var contact = (MapiContact)msg.ToMapiMessageItem();

        // Exibir alguns conteúdos na tela
        Console.WriteLine("Nome: " + contact.NameInfo.DisplayName);

        // Salvar em disco no formato VCard
        string contactName = contact.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        contact.Save($"{contactName}.vcf", ContactSaveFormat.VCard);
    }
}
```

Veja também: [Trabalhando com Listas de Distribuição](/email//net/working-with-distribution-lists-in-pst/)