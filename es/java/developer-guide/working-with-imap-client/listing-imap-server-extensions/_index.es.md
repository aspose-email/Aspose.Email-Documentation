---
title: "Listado de extensiones del servidor IMAP"
url: /es/java/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) te permite recuperar las extensiones del servidor que un servidor admite, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de utilizar el cliente para esa funcionalidad en particular. El método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getCapabilities--) devuelve los tipos de extensiones compatibles en forma de un arreglo de cadenas. El siguiente fragmento de código muestra cómo recuperar extensiones.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.gmail.com", "username", "password");
String[] getCapabilities = client.getCapabilities();
for (String getCap : getCapabilities) {
    System.out.println(getCap);
}
~~~