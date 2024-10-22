---
title: "Importando Correo Electrónico"
url: /es/net/importando-correo-electronico/
weight: 170
type: docs
---


## **VSTO**
A continuación se muestra el código para importar correo electrónico utilizando VSTO Outlook.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ImportEmail.msg";

 Outlook.MailItem email = (Outlook.MailItem)Application.Session.OpenSharedItem(FilePath);       

```
## **Aspose.Email**
A continuación se muestra el código para importar correo electrónico utilizando aspose.email para .NET.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ImportEmail.msg";  

 // cargando con opciones predeterminadas

  cargar desde msg

   MailMessage eml = MailMessage.Load(FilePath, new MsgLoadOptions());

```
## **Descargar Código Fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Import%20Email)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Ejemplo en Ejecución**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)