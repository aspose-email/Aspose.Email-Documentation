---
title: "Как запустить Aspose.Email"
url: /ru/net/how-to-run-aspose-email/
weight: 24
type: docs
---

Ниже мы предоставляем пошаговое руководство по настройке и запуску Aspose.Email на Linux и Windows, начиная с простого примера "Hello World".

Чтобы начать использовать библиотеку, просто следуйте этим шагам.

### **Hello World**

1. **Создайте новый проект**  
   Откройте Visual Studio и создайте новый проект Консольного приложения.

2. **Установите Aspose.Email**  
   Используйте NuGet Package Manager для установки Aspose.Email. Откройте консоль менеджера пакетов и выполните:

   ```
   Install-Package Aspose.Email
   ```

3. **Напишите код**

   Добавьте следующий код в ваш файл Program.cs:
   
   ```csharp
   
   using System;
   using Aspose.Email;
   
   class Program
   {
       static void Main(string[] args)
       {
           // Создайте новое сообщение электронной почты
            var eml = new MailMessage
            {
                Subject = "Hello World!",
                Body = "Это текст сообщения электронной почты.",
                // Укажите отправителя и получателя
                From = "sender@example.com",
                To = "recipient@example.com"
            };

            // Вывод сообщения
            Console.WriteLine("Тема: " + eml.Subject);
            Console.WriteLine("Текст: " + eml.Body);

            // Сохранить email в формате EML
            eml.Save("my.eml", SaveOptions.DefaultEml);
            
            // Сохранить email в формате MSG
            eml.Save("my.msg", SaveOptions.DefaultMsgUnicode);
       }
   }
   ```
4. **Запустите приложение**

   Запустите приложение. Вы должны увидеть тему и текст электронной почты, выведенные в консоль.

### **Запустите Aspose.Email для .NET на Linux**

Запуск Aspose.Email для .NET на Linux включает в себя настройку .NET-среды на вашем Linux-устройстве. Следуйте этим шагам:

1. **Установите .NET SDK**

   Загрузите и установите .NET SDK с официального сайта Microsoft .NET.
   
   Например, на Ubuntu вы можете установить .NET SDK, используя следующие команды:
   
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Создайте новый проект**

   Откройте терминал и создайте новое консольное приложение .NET:
   
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
   
3. **Добавьте пакет Aspose.Email**

   Добавьте Aspose.Email в ваш проект:
   
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Напишите код**
   Замените содержимое Program.cs кодом примера "Hello World", приведенным выше.

5. **Запустите приложение:**  
   Выполните приложение:

   ```bash
   dotnet run
   ```