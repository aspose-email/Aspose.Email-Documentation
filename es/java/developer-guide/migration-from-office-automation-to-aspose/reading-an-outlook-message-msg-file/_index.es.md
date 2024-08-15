---
title: "Lectura de un archivo de mensajes de Outlook (MSG)"
url: /es/java/reading-an-outlook-message-msg-file/
weight: 10
type: docs
---


{{% alert color="primary" %}}

Nuestros consejos de migración muestran cómo se pueden usar los productos de Aspose para mejorar sus aplicaciones y liberarlo de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo leer un archivo de mensajes de Microsoft Outlook y mostrar su contenido en la pantalla utilizando ambos [Automatización de Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java) código. El código de ejemplo que aparece a continuación solo muestra el contenido de la consola para que te hagas una idea de cómo funciona. Usa los fragmentos de código en tu propia aplicación de Windows, web u otra aplicación.

{{% /alert %}}
## **Automatización de oficinas**
Para usar objetos de automatización de oficina para Microsoft Outlook, debe agregar referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook a su proyecto.
### **Ejemplos de programación**
**C#**

~~~cs

// Add the namespaces

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Create a new Application Class

Application app = new Application();

// Create a MailItem object

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Access different fields of the message

System.Console.WriteLine(string.Format("Subject:{0}", item.Subject));

System.Console.WriteLine(string.Format("Sender Email Address:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("SenderName:{0}", item.SenderName));

System.Console.WriteLine(string.Format("TO:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Html Body:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Text Body:{0}", item.Body));


~~~
## **Aspose.Email para Java**
El siguiente fragmento de código hace lo mismo que [el código de arriba](/#office-automation) usando Aspose.Email para Java.

Para acceder al [Aspose.Enviar correo electrónico a Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) objetos, necesita agregar una referencia a Aspose.Email a su proyecto.
### **Ejemplos de programación**

~~~java

// Create a new object of type MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Access the fields of the message
System.out.println("Subject: " + msg.getSubject());
System.out.println("Sender Email Address: " + msg.getSenderEmailAddress());
System.out.println("SenderName:{0}" + msg.getSenderName());
System.out.println("TO:{0}" + msg.getDisplayTo());
System.out.println("CC:{0}" + msg.getDisplayCc());
System.out.println("BCC:{0}" + msg.getDisplayBcc());
System.out.println("Html Body:{0}" + msg.getBodyHtml());
System.out.println("Text Body:{0}" + msg.getBody());
System.out.println("Rtf Body:{0}" + msg.getBodyRtf());


~~~
