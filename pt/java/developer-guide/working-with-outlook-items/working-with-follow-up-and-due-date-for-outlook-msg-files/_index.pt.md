---
title: "Trabalhando com Sinalização de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook"
url: /pt/java/trabalhando-com-sinalizacao-de-acompanhamento-e-data-de-vencimento-para-arquivos-msg-do-outlook/
weight: 50
type: docs
---


## **Configurando Sinalização de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook**

Uma bandeira de acompanhamento marca uma mensagem de e-mail para algum tipo de ação. O Microsoft Outlook permite que os usuários sinalizem mensagens e, na configuração da bandeira, atribuam uma data de vencimento para o acompanhamento. O Microsoft Outlook envia um lembrete ao destinatário para lembrá-lo de acompanhar o e-mail. Sinalizar e-mails e definir datas de vencimento programaticamente permite que desenvolvedores de software automatizem certos tipos de e-mails e ajudem os destinatários a se lembrarem de agir. Por exemplo, poderia ser utilizado para enviar mensagens mensais a uma equipe de vendas para lembrá-los de completar seus relatórios; ou para enviar uma mensagem a todos os funcionários para lembrá-los de uma reunião da empresa. Aspose.Email para Java suporta a configuração de bandeira de acompanhamento e data de vencimento para os objetos [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) usando [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) e [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/). Existem várias variantes nas quais a bandeira de acompanhamento pode ser configurada em uma mensagem. Todas são utilizadas no exemplo de código abaixo:

1. Configurar uma bandeira de acompanhamento para uma mensagem
1. Adicionar uma data de vencimento e data de lembrete a uma mensagem
1. Adicionar uma bandeira à mensagem de um destinatário.
1. Marcar como completo.
1. Remover bandeira.
1. Ler opções de acompanhamento.
   
### **Configuração de uma bandeira de Acompanhamento**

O seguinte trecho de código mostra como configurar uma bandeira de acompanhamento.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de Arquivos.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Esta mensagem irá testar se opções de acompanhamento podem ser adicionadas a uma nova mensagem mapi.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Acompanhamento", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~

### **Configurando Acompanhamento para Destinatários**

O seguinte trecho de código mostra como configurar o acompanhamento para destinatários.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de Arquivos.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("Esta mensagem irá testar se opções de acompanhamento podem ser adicionadas a uma nova mensagem mapi.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // marcar esta mensagem como rascunho

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Adicionar a bandeira de acompanhamento para o destinatário agora
FollowUpManager.setFlagForRecipients(mapi, "Acompanhar", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~

### **Marcando uma bandeira de Acompanhamento como Completa**

O seguinte trecho de código mostra como marcar a bandeira de acompanhamento como completa.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de Arquivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~

### **Removendo uma bandeira de Acompanhamento**

O seguinte trecho de código mostra como remover a bandeira de acompanhamento.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de Arquivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~

### **Ler opções de bandeira de acompanhamento para uma mensagem**

O seguinte trecho de código mostra como ler as opções de bandeira de acompanhamento para uma mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de Arquivos.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~