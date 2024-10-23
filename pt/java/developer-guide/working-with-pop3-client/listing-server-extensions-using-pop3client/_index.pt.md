---
title: "Listando Extensões de Servidor usando Pop3Client"
url: /pt/java/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) permite que você recupere as extensões de servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getCapabilities--) retorna os tipos de extensão suportados na forma de um array de strings.

## **Recuperando Extensões de Servidor**

O seguinte exemplo de código demonstra como recuperar extensões de servidor usando Pop3Client para o servidor Gmail.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Connect and log in to POP3
Pop3Client client = new Pop3Client("pop.gmail.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setPort(995);
String[] getCaps = client.getCapabilities();
for (String item : getCaps) {
    System.out.println(item);
}
~~~