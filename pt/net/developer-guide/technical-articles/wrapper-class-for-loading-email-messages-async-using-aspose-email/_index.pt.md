---
title: "Classe Wrapper para carregar Mensagens de Email Assincronicamente usando Aspose.Email"
url: /pt/net/wrapper-class-for-loading-email-messages-async-using-aspose-email/
weight: 170
type: docs
---


## **Classe Wrapper para carregar Mensagens de Email**
Existem várias ocorrências onde é desejável ter funcionalidade de Timeout para abortar uma ação que está levando um tempo desnecessariamente longo. Este artigo fornece uma classe de exemplo para alcançar a funcionalidade de Timeout ao carregar arquivos EML/MSG que podem levar a atrasos muito longos ou falhar ao carregar. Como o Timeout não está diretamente relacionado a operações de leitura/gravação em disco ou rede, é de pouca utilidade implementar esse recurso dentro da API do que tê-lo implementado no lado do usuário escrevendo uma classe wrapper ao redor do Aspose.

Cancelar uma thread de longa duração pode ser alcançado com o uso de um delegado encapsulado que passa a thread, a ser finalizada, em uma variável local dentro do método que a iniciou. A thread de longa duração é cancelada abortando-a e o controle é retornado à aplicação principal. O seguinte exemplo de código fornece uma classe wrapper em torno da biblioteca Aspose.Email. O código também segue um exemplo de uso da classe wrapper.
### **Exemplo de Programação com .NET 3.5 e acima**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage-WrapperMailMessage.cs" >}}
### **Exemplo de Programação com .NET 2.0**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage_2_0-WrapperMailMessage.cs" >}}
### **Exemplo de Uso**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-UsingMailMessageWrapper-UsingMailMessageWrapper.cs" >}}