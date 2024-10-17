---
title: "Cómo Ejecutar Aspose.Email"
url: /es/net/how-to-run-aspose-email/
weight: 24
type: docs
---

A continuación, proporcionamos una guía paso a paso para configurar y ejecutar Aspose.Email en Linux y Windows, comenzando con un ejemplo simple de "Hola Mundo".

Para comenzar a utilizar la biblioteca, simplemente siga los pasos.

### **Hola Mundo**

1. **Crear un Nuevo Proyecto** 
   Abra Visual Studio y cree un nuevo proyecto de Aplicación de Consola.

2. **Instalar Aspose.Email** 
   Use el Administrador de Paquetes NuGet para instalar Aspose.Email. Abra la Consola del Administrador de Paquetes y ejecute:

   ```
   Install-Package Aspose.Email
   ```

3. **Escribir el Código**

   Agregue el siguiente código a su archivo Program.cs:
   
   ```csharp
   
   using System;
   using Aspose.Email;
   
   class Program
   {
       static void Main(string[] args)
       {
           // Crear un nuevo mensaje de correo electrónico
            var eml = new MailMessage
            {
                Subject = "¡Hola Mundo!",
                Body = "Este es el cuerpo del correo electrónico.",
                // Especificar el remitente y el destinatario
                From = "sender@example.com",
                To = "recipient@example.com"
            };

            // Mostrar el mensaje
            Console.WriteLine("Asunto: " + eml.Subject);
            Console.WriteLine("Cuerpo: " + eml.Body);

            // Guardar correo electrónico en formato EML
            eml.Save("my.eml", SaveOptions.DefaultEml);
            
            // Guardar correo electrónico en formato MSG
            eml.Save("my.msg", SaveOptions.DefaultMsgUnicode);
       }
   }
   ```
4. **Ejecutar la Aplicación**

   Ejecute la aplicación. Debería ver el asunto y el cuerpo del correo electrónico impresos en la consola.

### **Ejecutar Aspose.Email para .NET en Linux**

Ejecutar Aspose.Email para .NET en Linux implica configurar un entorno .NET en su máquina Linux. Siga estos pasos:

1. **Instalar .NET SDK**

   Descargue e instale el SDK de .NET desde el sitio web oficial de Microsoft .NET.
   
   Por ejemplo, en Ubuntu, puede instalar el SDK de .NET utilizando los siguientes comandos:
   
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Crear un Nuevo Proyecto**

   Abra una terminal y cree una nueva Aplicación de Consola .NET:
   
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
   
3. **Agregar el Paquete Aspose.Email**

   Agregue Aspose.Email a su proyecto:
   
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Escribir el Código**
   Reemplace el contenido de Program.cs con el código de ejemplo "Hola Mundo" proporcionado anteriormente.

5. **Ejecutar la Aplicación:**
   Ejecute la aplicación:

   ```bash
   dotnet run
   ```