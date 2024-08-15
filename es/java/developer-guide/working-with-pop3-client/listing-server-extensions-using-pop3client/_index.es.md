---
title: "Listado de extensiones de servidor mediante Pop3Client"
url: /es/java/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getCapabilities--) El método devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.

## **Recuperación de extensiones de servidor**

El siguiente ejemplo de código muestra cómo recuperar extensiones de servidor mediante el servidor Pop3Client para Gmail.

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
