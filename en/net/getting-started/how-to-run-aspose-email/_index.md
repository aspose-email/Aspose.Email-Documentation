---
title: How to Run Aspose.Email
ArticleTitle: How to Run Aspose.Email
type: docs
weight: 24
url: /net/how-to-run-aspose-email/
---

Below, we provide a step-by-step guide for setting up and running Aspose.Email on Linux and Windows, starting with a simple "Hello World" example.

To start utilizing the library, just follow the steps.

### **Hello World**

1. **Create a New Project** 
   Open Visual Studio and create a new Console Application project.

2. **Install Aspose.Email** 
   Use NuGet Package Manager to install Aspose.Email. Open the Package Manager Console and run:

   ```
   Install-Package Aspose.Email
   ```

3. **Write the Code**

   Add the following code to your Program.cs file:
   
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
                Subject = "Hello World!",
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
4. **Run the Application**

   Execute the application. You should see the email subject and body printed to the console.

### **Run Aspose.Email for .NET on Linux**

Running Aspose.Email for .NET on Linux involves setting up a .NET environment on your Linux machine. Follow these steps:

1. **Install .NET SDK**

   Download and install the .NET SDK from the official Microsoft .NET website.
   
   For example, on Ubuntu, you can install the .NET SDK using the following commands:
   
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Create a New Project**

   Open a terminal and create a new .NET Console Application:
   
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
   
3. **Add Aspose.Email Package**

   Add Aspose.Email to your project:
   
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Write the Code**
   Replace the content of Program.cs with the "Hello World" example code provided above.

5. **Run the Application:**
   Execute the application:

   ```bash
   dotnet run
   ```


