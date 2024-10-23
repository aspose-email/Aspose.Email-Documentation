---
title: "Trabalhando com Regras no Exchange Server"
url: /pt/java/trabalhando-com-regras-no-exchange-server/
weight: 90
type: docs
---


## **Gerenciando Regras**
Aspose.Email para Java pode ser usado para gerenciar as regras no Exchange Server usando a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta classe utiliza os Serviços Web do Exchange (EWS), que estão disponíveis no Exchange Server 2007 e versões posteriores. Para mostrar como gerenciar regras, este artigo explica como:

- Ler as regras já no servidor.
- Criar uma nova regra.
- Atualizar uma regra existente.

O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo.
### **Ler Regras**
Para obter todas as regras do Exchange Server:

1. Conecte-se a um Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.getInboxRules() para obter todas as regras.
1. Em um loop foreach, percorra todas as regras e exiba as propriedades da regra, como condições, ações e nome.

O seguinte trecho de código mostra como ler regras.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado ao servidor Exchange");

// Obter todas as Regras da Caixa de Entrada
InboxRule[] inboxRules = client.getInboxRules();

// Exibir informações sobre cada regra
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Nome de Exibição: " + inboxRule.getDisplayName());

    // Verificar se há uma condição de "Endereço Remetente"
    if (inboxRule.getConditions().getFromAddresses().size() > 0) {
        for (MailAddress fromAddress : (Iterable<MailAddress>) inboxRule.getConditions().getFromAddresses()) {
            System.out.println("De: " + fromAddress.getDisplayName() + " - " + fromAddress.getAddress());
        }
    }
    // Verificar se há uma condição de "Assunto Contém"
    if (inboxRule.getConditions().containsSubjectStrings().size() > 0) {
        // conversão de foreach para while
        for (String subject : inboxRule.getConditions().containsSubjectStrings()) {
            System.out.println("Assunto contém: " + subject);
        }
    }
    // Verificar se há uma ação de "Mover para Pasta"
    if (inboxRule.getActions().getMoveToFolder().length() > 0) {
        System.out.println("Mover mensagem para pasta: " + inboxRule.getActions().getMoveToFolder());
    }
}
~~~  
### **Criando uma Nova Regra**
Para criar uma nova regra no Exchange Server, execute os seguintes passos:

1. Conecte-se a um Exchange Server usando a classe IEWSClient.
1. Crie uma nova instância da classe InboxRule e defina as seguintes propriedades obrigatórias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Chame o método IEWSClient.createInboxRule() para criar a regra.

O seguinte trecho de código mostra como criar uma nova regra.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado ao servidor Exchange");

InboxRule rule = new InboxRule();
rule.setDisplayName("Mensagem do cliente ABC");

// Adicionar condições
RulePredicates newRules = new RulePredicates();
// Definir Assunto contém a string "ABC" e adicionar as condições
newRules.containsSubjectStrings().addItem("ABC");
newRules.getFromAddresses().addMailAddress(new MailAddress("administrator@ex2010.local", true));
rule.setConditions(newRules);

// Adicionar Ações e Mover a mensagem para uma pasta
RuleActions newActions = new RuleActions();
newActions.setMoveToFolder("120:AAMkADFjMjNjMmNjLWE3NzgtNGIzNC05OGIyLTAwNTgzNjRhN2EzNgAuAAAAAABbwP+Tkhs0TKx1GMf0D/cPAQD2lptUqri0QqRtJVHwOKJDAAACL5KNAAA=AQAAAA==");
rule.setActions(newActions);
client.createInboxRule(rule);
~~~  
### **Atualizando uma Regra**
Para atualizar uma regra no Exchange Server:

1. Conecte-se a um Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.getInboxRules() para obter todas as regras.
1. Em um loop foreach, percorra todas as regras e obtenha a regra que deseja alterar, correspondendo o DisplayName em uma condição.
1. Atualize as propriedades da regra.
1. Chame o método IEWSClient.updateInboxRule() para atualizar a regra.

O seguinte trecho de código mostra como atualizar uma regra.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado ao servidor Exchange");

// Obter todas as Regras da Caixa de Entrada
InboxRule[] inboxRules = client.getInboxRules();

// Loop através de cada regra
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Nome de Exibição: " + inboxRule.getDisplayName());
    if ("Mensagem do cliente ABC".equals(inboxRule.getDisplayName())) {
        System.out.println("Atualizando a regra....");
        inboxRule.getConditions().getFromAddresses().set_Item(0, new MailAddress("administrator@ex2010.local", true));
        client.updateInboxRule(inboxRule);
    }
}
~~~