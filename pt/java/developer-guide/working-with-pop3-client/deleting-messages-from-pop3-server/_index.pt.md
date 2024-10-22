---
title: "Deletando Mensagens do Servidor POP3"
url: /pt/java/deletando-mensagens-do-servidor-pop3/
weight: 20
type: docs
---


Aspose.Email é um componente robusto que permite realizar operações personalizadas após certas ações. Aspose.Email dispara muitos eventos sobre os quais os usuários podem realizar operações. Esse recurso fornece aos usuários mais controle sobre seu aplicativo. Por exemplo, os usuários podem realizar as ações desejadas quando:

- Todos os e-mails em massa foram enviados.
- Uma mensagem está prestes a ser enviada.
- Um e-mail foi completamente enviado.
- Quando um destinatário é rejeitado pelo servidor SMTP.

Caixas de correio POP3 residem em um servidor POP3. O e-mail nessas caixas de correio pode ser recuperado para seu PC por meio do [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). A classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) usa o protocolo POP3 para copiar as mensagens de correio da sua caixa de correio POP3 para o seu PC. Uma vez que o e-mail foi recuperado, você não precisa estar conectado à internet enquanto ele está sendo lido, pois você pode ler o e-mail recuperado no seu PC. Se você não precisar ou quiser uma cópia de algumas mensagens de e-mail mantidas no servidor POP3, você pode deletá-las. Esta seção mostra como deletar e-mails usando a classe [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

## **Deletar um E-mail pelo Índice**

O seguinte trecho de código deleta todas as mensagens de um caixa de correio uma a uma, com base em seu índice. O índice nunca deve ser <=0 em [Pop3Client.deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#deleteMessage-int-).

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java

// Crie um cliente POP3
Pop3Client client = new Pop3Client("mail.aspose.com", 110, "username", "psw");
try {
    // Delete todas as mensagens uma a uma
    int messageCount = client.getMessageCount();
    for (int i = 1; i <= messageCount; i++) {
        client.deleteMessage(i);
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Deletar Todos os E-mails**

Nós também podemos chamar [Pop3Client.deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) para deletar todas as mensagens. O seguinte trecho de código mostra como deletar todos os e-mails.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java

// Deletar todas as mensagens
client.deleteMessages();
~~~

Se a conexão com o servidor POP3 for interrompida imediatamente após as operações de deletação, você não poderá mais chamar [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).cancelDeletes() para realizar as ações que você deseja.

## **Cancelar Deletões**

[Pop3Client.undeleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) pode ser usado para cancelar a deletação de mensagens de e-mail. O seguinte trecho de código mostra como cancelar deletões.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java

// Cancelar deletões
client.undeleteMessages();
~~~