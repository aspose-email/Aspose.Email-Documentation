---
title: "Trabalhando com Configuração de Usuário no Servidor"
url: /pt/java/trabalhando-com-configuracao-de-usuario-no-servidor/
weight: 110
type: docs
---


## **Gerenciando a Configuração do Usuário**
Aspose.Email para Java pode ser utilizado para gerenciar a configuração do usuário em um Exchange Server com a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis apenas nas versões 2007 e posteriores do Exchange Server. Neste artigo, veremos como ler, criar, atualizar e excluir configurações de usuário no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo. O seguinte trecho de código mostra como se conectar ao Exchange Server 2010 em todos os exemplos deste artigo.



~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@ASE305.onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
### **Lendo a Configuração do Usuário**
Para obter as informações de configuração do usuário de uma pasta específica do Exchange Server:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.getUserConfiguration() para obter a configuração do usuário para uma pasta.
1. Exiba as propriedades da configuração do usuário, como ID, nome e itens do dicionário como pares de chave-valor.

O seguinte trecho de código mostra como ler a configuração do usuário.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Conectado ao Exchange 2010");

// Obter a Configuração do Usuário para a pasta Caixa de Entrada
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);

System.out.println("Id da Configuração: " + userConfig.getId());
System.out.println("Nome da Configuração: " + userConfig.getUserConfigurationName().getName());
System.out.println("Pares de chave-valor:");
// conversão de foreach para while
for (Object key : userConfig.getDictionary().keySet()) {
    System.out.println(key + ": " + userConfig.getDictionary().get(key).toString());
}
~~~
### **Criando Configurações de Usuário**
Para criar a configuração do usuário para uma pasta específica em um Exchange Server:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.createUserConfiguration() para criar a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como criar configurações de usuário.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Conectado ao Exchange 2010");

// Criar a Configuração do Usuário para a pasta Caixa de Entrada
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = new UserConfiguration(userConfigName);
userConfig.getDictionary().put("key1", "value1");
userConfig.getDictionary().put("key2", "value2");
userConfig.getDictionary().put("key3", "value3");
client.createUserConfiguration(userConfig);
~~~
### **Atualizando a Configuração do Usuário**
Para atualizar a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.updateUserConfiguration() para atualizar a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como atualizar a configuração do usuário.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Conectado ao Exchange 2010");

// Criar a Configuração do Usuário para a pasta Caixa de Entrada
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);
userConfig.setId(null);

// Atualizar Configuração do Usuário
userConfig.getDictionary().put("key1", "new-value1");
client.updateUserConfiguration(userConfig);
~~~
### **Excluindo a Configuração do Usuário**
Para excluir a configuração do usuário para uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.deleteUserConfiguration() para excluir a configuração do usuário para uma pasta.

O seguinte trecho de código mostra como excluir a configuração do usuário.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado ao Exchange 2010");

// Excluir Configuração do Usuário
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~