---
title: "Trabalhando com Sinais de Mensagem no Servidor"
url: /pt/java/trabalhando-com-sinais-de-mensagem-no-servidor/
weight: 30
type: docs
---


## **Mudando os Sinais da Mensagem**

Você pode mudar os sinais da mensagem usando o método [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Este método leva dois parâmetros.

1. O número de sequência da mensagem ou ID único.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

Os seguintes sinais podem ser configurados:

- [Answered](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Deleted](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Draft](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Empty](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Flagged](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [isRead](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Recent](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
  
### **Configurando Sinais da Mensagem**

O seguinte trecho de código mostra como mudar os sinais da mensagem em um servidor IMAP com Aspose.Email.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Marcar a mensagem como lida
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Removendo Sinais da Mensagem**

Os sinais da mensagem também podem ser removidos com o método [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). O uso é similar ao do método [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Ele leva um número de sequência ou ID único da mensagem e [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). O seguinte trecho de código mostra como remover os sinais da mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Remover o sinal da mensagem
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Configurando Sinais Personalizados**

Você também pode definir sinais personalizados para uma mensagem usando o [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) da API. O ImapClient [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) fornece a capacidade de definir sinais personalizados nas mensagens.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Criar uma mensagem
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "assunto", "mensagem");

// Adicionar a mensagem à caixa de entrada
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Adicionar sinais personalizados à mensagem adicionada
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Recuperar as mensagens para verificar a presença do sinal personalizado
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Palavra-chave encontrada");
}
~~~