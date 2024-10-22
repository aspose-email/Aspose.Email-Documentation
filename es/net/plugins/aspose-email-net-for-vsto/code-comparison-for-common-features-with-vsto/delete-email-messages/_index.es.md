---
title: "Eliminar Mensajes de Correo Electrónico"
url: /es/net/delete-email-messages/
weight: 100
type: docs
---


## **VSTO**
A continuación se muestra el código para eliminar mensajes utilizando VSTO Outlook.

``` cs

  // Crear clase de Aplicación y obtener espacio de nombres

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Obtener información de la Bandeja de Entrada en objeto de tipo MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.Delete();      

```
## **Aspose.Email**
A continuación se muestra el código para eliminar mensajes utilizando aspose.email para .NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Crear instancia de la clase ExchangeClient dando credenciales

 ExchangeClient client = new ExchangeClient(MailBoxURI, UserName, Password, Domain);

 // Llamar al método ListMessages para listar información de mensajes de la Bandeja de Entrada

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 // Obtener URI del Mensaje a Eliminar

 string MessageURI= msgCollection[0].UniqueUri;

 // Eliminar el mensaje

 client.DeleteMessage(MessageURI);

```
## **Descargar Código Fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Ejemplo en Ejecución**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)