---
title: "Trabalhando com Pop3Client Assincronamente"
url: /pt/java/trabalhando-com-pop3client-assincronamente/
weight: 60
type: docs
---

## **Trabalhando com Pop3Client Assincronamente**

As mensagens também podem ser recuperadas de caixas de entrada de forma assíncrona usando o [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) da Aspose.Email. Este artigo mostra como recuperar mensagens de uma caixa de entrada de forma assíncrona. Ele também mostra como listar mensagens fornecendo critérios de pesquisa usando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

### **Recuperando Mensagens Assincronamente**

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
client.setHost("pop.gmail.com");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.SSLImplicit);
client.setUsername("username");
client.setPassword("password");

try {
    Pop3MessageInfoCollection messages = client.listMessages();
    System.out.println("Número Total de Mensagens na caixa de entrada:" + messages.size());
    IAsyncResult asyncResult = client.beginFetchMessage(messages.get_Item(0).getSequenceNumber());
    MailMessage message = client.endFetchMessage(asyncResult);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

### **Listar Mensagens Assincronamente com MailQuery**

A classe [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) pode ser usada para especificar critérios de pesquisa para recuperar uma lista de mensagens assíncronamente, como mostrado no seguinte exemplo de código.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java

MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Subject");
MailQuery query = builder.getQuery();
IAsyncResult asyncResult = client.beginListMessages(query);
Pop3MessageInfoCollection messages = client.endListMessages(asyncResult);
~~~