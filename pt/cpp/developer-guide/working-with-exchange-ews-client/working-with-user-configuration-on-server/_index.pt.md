---
title: "Trabalhando com Configuração do Usuário no Servidor"
url: /pt/cpp/trabalhando-com-configuracao-do-usuario-no-servidor/
weight: 110
type: docs
---

## **Gerenciando Configuração do Usuário**
A API Aspose.Email pode ser usada para gerenciar a configuração do usuário em um Exchange Server com a classe [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis apenas no Exchange Server 2007 e versões posteriores. Neste artigo, veremos como ler, criar, atualizar e excluir configurações de usuário no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo. O seguinte trecho de código mostra como conectar ao Exchange Server 2010 em todos os exemplos deste artigo.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Lendo Configuração do Usuário**
Para obter as informações de configuração do usuário de uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Chame o método [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111) para obter a configuração do usuário para uma pasta.
1. Exiba as propriedades da configuração do usuário como ID, nome e itens de dicionário como pares chave-valor.

O seguinte trecho de código mostra como ler a configuração do usuário.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Criando Configurações do Usuário**
Para criar a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Chame o método [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db) para criar a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como criar configurações do usuário.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Atualizando Configuração do Usuário**
Para atualizar a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Chame o método [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e) para atualizar a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como atualizar a configuração do usuário.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Excluindo Configuração do Usuário**
Para excluir a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Chame o método [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c) para excluir a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como excluir a configuração do usuário.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}