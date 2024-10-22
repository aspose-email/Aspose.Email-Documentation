---
title: "Listagem de Extensões do Servidor IMAP"
url: /pt/java/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) permite que você recupere as extensões do servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda na identificação da disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getCapabilities--) retorna os tipos de extensão suportados na forma de um array de strings. O seguinte trecho de código mostra como recuperar extensões.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.gmail.com", "username", "password");
String[] getCapabilities = client.getCapabilities();
for (String getCap : getCapabilities) {
    System.out.println(getCap);
}
~~~