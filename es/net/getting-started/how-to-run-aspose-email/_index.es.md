---
title: "Cómo ejecutar Aspose.Email"
url: /es/net/how-to-run-aspose-email/
weight: 24
type: docs
---

A continuación, proporcionamos una guía paso a paso para configurar y ejecutar Aspose.Email en Linux y Windows, comenzando con un sencillo ejemplo de «Hola mundo».

Para empezar a utilizar la biblioteca, solo tienes que seguir los pasos.

### **Hola mundo**

1. **Crear un proyecto nuevo**
   Abra Visual Studio y cree un nuevo proyecto de aplicación de consola.

2. **Instale Aspose.Email**
   Use NuGet Package Manager para instalar Aspose.Email. Abra la consola del administrador de paquetes y ejecute:

   ```
   Install-Package Aspose.Email
   ```

3. **Escribe el código**

   Agregue el siguiente código a su archivo Program.cs:
  
   ```csharp
  
   using System;
   using Aspose.Email;
  
   class Program
   {
       static void Main(string[] args)
       {
           // Create a new email message
            var eml = new MailMessage
            {
                Subject = "Hola mundo!",
                Body = "This is the body of the email.",
                // Specify sender and recipient
                From = "sender@example.com",
                To = "recipient@example.com"
            };

            // Display the message
            Console.WriteLine("Subject: " + eml.Subject);
            Console.WriteLine("Body: " + eml.Body);

            // Save email in EML format
            eml.Save("my.eml", SaveOptions.DefaultEml);
           
            // Save email in MSG format
            eml.Save("my.msg", SaveOptions.DefaultMsgUnicode);
       }
   }
   ```
4. **Ejecute la aplicación**

   Ejecute la aplicación. Deberías ver el asunto y el cuerpo del correo electrónico impresos en la consola.

### **Ejecute Aspose.Email para.NET en Linux**

La ejecución de Aspose.Email para.NET en Linux implica configurar un entorno.NET en su máquina Linux. Siga estos pasos:

1. **Instalar el SDK de.NET**

   Descargue e instale el SDK de.NET desde el sitio web oficial de Microsoft.NET.
  
   Por ejemplo, en Ubuntu, puedes instalar el SDK de.NET con los siguientes comandos:
  
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Crear un proyecto nuevo**

   Abra una terminal y cree una nueva aplicación de consola de.NET:
  
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
  
3. **Agregar paquete Aspose.Email**

   Añade Aspose.Email a tu proyecto:
  
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Escribe el código**
   Sustituya el contenido de Program.cs por el código de ejemplo «Hola mundo» proporcionado anteriormente.

5. **Ejecute la aplicación:**
   Ejecute la aplicación:

   ```bash
   dotnet run
   ```


