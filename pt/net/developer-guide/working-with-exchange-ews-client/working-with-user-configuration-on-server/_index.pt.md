---
title: "Trabalhando com Configuração de Usuário no Servidor"
url: /pt/net/trabalhando-com-configuracao-de-usuario-no-servidor/
weight: 110
type: docs
---


## **Gerenciando Configuração de Usuário**

Aspose.Email para .NET pode ser usado para gerenciar a configuração do usuário em um Exchange Server com a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis apenas no Exchange Server 2007 e versões posteriores. Neste artigo, veremos como ler, criar, atualizar e excluir configurações de usuário no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo. O seguinte snippet de código mostra como se conectar ao Exchange Server 2010 em todos os exemplos deste artigo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

### **Lendo Configuração de Usuário**

Para obter as informações de configuração do usuário de uma pasta específica do Exchange Server:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration) para obter a configuração do usuário de uma pasta.
1. Exiba as propriedades de configuração do usuário, como ID, nome e itens do dicionário como pares chave-valor.

O seguinte snippet de código mostra como ler a configuração do usuário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

### **Criando Configurações de Usuários**

Para criar a configuração do usuário para uma pasta específica em um Exchange Server:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration) para criar a configuração do usuário para uma pasta.

O seguinte snippet de código mostra como criar configurações de usuários.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

### **Atualizando Configuração de Usuário**

Para atualizar a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration) para atualizar a configuração do usuário para uma pasta.

O seguinte snippet de código mostra como atualizar a configuração do usuário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

### **Excluindo Configuração de Usuário**

Para excluir a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration) para excluir a configuração do usuário para uma pasta.

O seguinte snippet de código mostra como excluir a configuração do usuário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}