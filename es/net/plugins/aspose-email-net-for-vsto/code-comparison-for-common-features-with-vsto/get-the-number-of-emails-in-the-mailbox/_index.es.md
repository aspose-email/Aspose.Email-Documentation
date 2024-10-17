---
title: "Obtener el número de correos electrónicos en la bandeja de entrada"
url: /es/net/get-the-number-of-emails-in-the-mailbox/
weight: 140
type: docs
---


## **VSTO**
A continuación se muestra el código para obtener los correos electrónicos en la bandeja de entrada utilizando VSTO Outlook.

``` cs

  // Crear clase Application y obtener espacio de nombres

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Obtener información de la bandeja de entrada en un objeto de tipo MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 int i = inbox.Items.Count;

 MessageBox.Show("Cuenta de mensajes: " + i);

```
## **Aspose.Email**
A continuación se muestra el código para obtener los correos electrónicos en la bandeja de entrada utilizando aspose.email para .NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "usuario";

 string Password = "contraseña";

 string Domain = "dominio";

 // Crear instancia de la clase ExchangeClient proporcionando credenciales

 ExchangeClient client = new ExchangeClient(MailBoxURI,UserName, Password, Domain);

 // Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 int i = msgCollection.Count;

 Console.WriteLine("Cuenta de mensajes: " + i);

```
## **Descargar código fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Get%20the%20number%20of%20emails%20in%20the%20mailbox)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar ejemplo en funcionamiento**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)