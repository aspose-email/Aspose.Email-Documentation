---
title: "Listando extensiones de servidor usando Pop3Client"
url: /es/java/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) te permite recuperar las extensiones del servidor que un servidor soporta, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad particular. El método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getCapabilities--) devuelve los tipos de extensión soportados en forma de un array de cadenas.

## **Recuperando extensiones del servidor**

El siguiente ejemplo de código demuestra la recuperación de extensiones del servidor usando Pop3Client para el servidor Gmail.

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