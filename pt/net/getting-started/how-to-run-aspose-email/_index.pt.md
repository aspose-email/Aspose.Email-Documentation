---
title: "Como Executar Aspose.Email"
url: /pt/net/how-to-run-aspose-email/
weight: 24
type: docs
---

Abaixo, fornecemos um guia passo a passo para configurar e executar o Aspose.Email no Linux e no Windows, começando com um exemplo simples de "Olá Mundo".

Para começar a utilizar a biblioteca, basta seguir os passos.

### **Olá Mundo**

1. **Criar um Novo Projeto**  
   Abra o Visual Studio e crie um novo projeto de Aplicativo de Console.

2. **Instalar Aspose.Email**  
   Use o Gerenciador de Pacotes NuGet para instalar o Aspose.Email. Abra o Console do Gerenciador de Pacotes e execute:

   ```
   Install-Package Aspose.Email
   ```

3. **Escrever o Código**

   Adicione o seguinte código ao seu arquivo Program.cs:
   
   ```csharp
   
   using System;
   using Aspose.Email;
   
   class Program
   {
       static void Main(string[] args)
       {
           // Crie uma nova mensagem de e-mail
            var eml = new MailMessage
            {
                Subject = "Olá Mundo!",
                Body = "Este é o corpo do e-mail.",
                // Especifique o remetente e o destinatário
                From = "sender@example.com",
                To = "recipient@example.com"
            };

            // Exiba a mensagem
            Console.WriteLine("Assunto: " + eml.Subject);
            Console.WriteLine("Corpo: " + eml.Body);

            // Salve o e-mail no formato EML
            eml.Save("my.eml", SaveOptions.DefaultEml);
            
            // Salve o e-mail no formato MSG
            eml.Save("my.msg", SaveOptions.DefaultMsgUnicode);
       }
   }
   ```
4. **Executar o Aplicativo**

   Execute o aplicativo. Você deve ver o assunto e o corpo do e-mail impressos no console.

### **Executar Aspose.Email para .NET no Linux**

Executar o Aspose.Email para .NET no Linux envolve configurar um ambiente .NET na sua máquina Linux. Siga estes passos:

1. **Instalar o SDK do .NET**

   Baixe e instale o SDK do .NET no site oficial da Microsoft .NET.
   
   Por exemplo, no Ubuntu, você pode instalar o SDK do .NET usando os seguintes comandos:
   
   ```bash
   wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
   sudo dpkg -i packages-microsoft-prod.deb
   sudo apt-get update
   sudo apt-get install -y apt-transport-https
   sudo apt-get update
   sudo apt-get install -y dotnet-sdk-6.0
   ```
2. **Criar um Novo Projeto**

   Abra um terminal e crie um novo Aplicativo de Console .NET:
   
   ```bash
   dotnet new console -n HelloWorldAspose
   cd HelloWorldAspose
   ```
   
3. **Adicionar o Pacote Aspose.Email**

   Adicione o Aspose.Email ao seu projeto:
   
   ```bash
   dotnet add package Aspose.Email
   ```

4. **Escrever o Código**  
   Substitua o conteúdo de Program.cs pelo código do exemplo "Olá Mundo" fornecido acima.

5. **Executar o Aplicativo:**  
   Execute o aplicativo:

   ```bash
   dotnet run
   ```