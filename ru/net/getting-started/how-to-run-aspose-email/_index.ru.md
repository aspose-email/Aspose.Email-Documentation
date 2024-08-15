---
title: "Как запустить Aspose.Email"
url: /ru/net/how-to-run-aspose-email/
weight: 24
type: docs
---

Ниже мы приводим пошаговое руководство по настройке и запуску Aspose.Email в Linux и Windows, начиная с простого примера «Привет, мир».

Чтобы начать использовать библиотеку, просто следуйте инструкциям.

### **Привет, мир**

1. **Создайте новый проект**
   Откройте Visual Studio и создайте новый проект консольного приложения.

2. **Установите Aspose.Email**
   Используйте диспетчер пакетов NuGet для установки Aspose.Email. Откройте консоль диспетчера пакетов и запустите:

   ```
   Install-Package Aspose.Email
   ```

3. **Напишите код**

   Добавьте следующий код в файл Program.cs:
  
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
                Subject = "Привет, мир!",
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
4. **Запустите приложение**

   Выполните приложение. Вы должны увидеть тему и текст письма, напечатанные на консоли.

### **Запустите программу Aspose.Email для платформы.NET в Linux**

Запуск Aspose.Email для .NET в Linux включает настройку среда.NET на вашем компьютере под управлением Linux. Выполните следующие шаги:

1. **Установите .NET SDK**

   Скачайте и установите .NET SDK с официального веб-сайта Microsoft .NET.
  
   Например, в Ubuntu вы можете установить .NET SDK с помощью следующих команд:
  
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Создайте новый проект**

   Откройте терминал и создайте новое консольное приложение.NET:
  
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
  
3. **Добавить пакет Aspose.Email**

   Добавьте Aspose.Email в свой проект:
  
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Напишите код**
   Замените содержимое файла Program.cs приведенным выше примером кода «Привет, мир».

5. **Запустите приложение:**
   Выполните приложение:

   ```bash
   dotnet run
   ```


