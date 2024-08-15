---
title: "Introducción y ejemplos de aplicaciones"
url: /es/java/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Escenarios de uso del correo de Aspose.Email**
Este artículo sugiere varios usos posibles de Aspose.Email para Java, centrándose en particular en las funciones de programación de correo electrónico del componente.
### **Software para boletines**
La API de correo Aspose.Email se puede usar para crear una aplicación sólida de boletines. Con la compatibilidad de Aspose.Email para agregar objetos incrustados (como imágenes, sonidos, etc.), es posible crear boletines HTML enriquecidos con imágenes (y otros objetos incrustados). Con la función de correo masivo de la API de correo de Aspose.Email, también es posible enviar grandes cantidades de correos electrónicos masivos en un período de tiempo limitado. Aspose.Email Mail también proporciona una función de combinación de correspondencia basada en plantillas que se puede utilizar para crear una plantilla de boletín informativo. La plantilla de boletín se puede usar para realizar una combinación de correspondencia para enviar boletines masivos. Hay muchas otras tareas posibles que Aspose.Email Mail puede realizar en una aplicación de marketing por correo electrónico.
### **Otras herramientas de marketing**
Al igual que las aplicaciones de boletines informativos, se pueden crear muchos otros tipos de software con Aspose.Email Mail. Úselo para crear marketing por correo electrónico, correo masivo y correo masivo para campañas electrónicas, y más.
### **Aplicaciones empresariales**
Aspose.Email Mail se puede usar en casi todo tipo de aplicaciones empresariales para realizar tareas de utilidad:

- Alertas por correo electrónico: envíe alertas por correo electrónico para informar a los usuarios sobre las actividades.
- Solicitudes de reunión: envíe solicitudes de reuniones de negocios mediante el soporte iCalendar de Aspose.Email Mail.
- Informes programados por correo electrónico: los informes son parte integral de la mayoría de las aplicaciones empresariales. Muchos informes empresariales se generan a intervalos. Utilice Aspose.Email Mail para enviar por correo electrónico los informes programados.
### **Clientes de correo electrónico**
Aspose.Email Mail también se puede usar en clientes de correo electrónico para enviar correos electrónicos normales. Admite archivos adjuntos, objetos incrustados, eventos de iCalendar, combinaciones de correspondencia, enviar correos electrónicos masivos, etc., por lo que Aspose.Email Mail es la mejor opción para crear aplicaciones de clientes de correo electrónico.
## **Ejemplo de aplicación de correo Aspose.Email**
Para ilustrar cómo usar Aspose.Email Mail, crearemos una aplicación que demuestre cómo crear un mensaje de correo electrónico con [Clase MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) y luego envíelo usando la clase SmtpClient.
### **Correo: ejemplos de pasos de solicitud**
Siga los pasos que se indican a continuación para crear una aplicación con Aspose.Email.

1. Diseñe su aplicación: cree una interfaz que ocupe tres campos: **From**, **To** and **Message**.
1. Haga doble clic en **Send** pulse el botón en la vista de diseño y escriba su código en el editor.
1. Crea una instancia de la clase MailMessage y usa sus propiedades para crear un mensaje de correo electrónico. (Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante la clase SmtpClient).
1. Crea una instancia de la clase SmtpClient y usa sus propiedades para enviar un mensaje de correo electrónico.
1. Pruebe su aplicación.
1. Escriba las direcciones en **From** and **To** fields.
1. Escriba un mensaje en **Cuerpo del mensaje** field.
1. Click **Send**.

Los pasos anteriores se describen a continuación, haga doble clic en **Send** botón en la vista de diseño y añada el siguiente código:



~~~Java
// Declare message as MailMessage instance
MailMessage message = new MailMessage();
// Specify From, To, Subject and Body
message.setFrom(new MailAddress("#From"));
message.setTo(MailAddressCollection.to_MailAddressCollection("#To"));
message.setSubject("#Subject");
message.setBody("#Body");

// Send email using SmtpClient, Create an instance of the SmtpClient Class and Specify the mailing host server, Username, Password and Port
SmtpClient client = new SmtpClient();

// Specify the mailing host server, Username, Password and Port
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(25);
client.send(message);

// Notify the user that a message has been sent
System.out.println("Message Sent");
~~~


Al conectarnos a un servidor con SSL habilitado, necesitamos establecer las siguientes propiedades del objeto SMTPClient:



~~~Java
// Set the port to 587. This is the SSL port of Gmail SMTP server, set the security mode to explicit
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~
### **Conclusion**
Aspose.Email Mail es un componente muy potente con el que los desarrolladores pueden realizar prácticamente tareas de correo electrónico, como enviar correos electrónicos masivos con varios subprocesos, combinar correspondencia, añadir archivos adjuntos, incrustar imágenes y sonidos en los mensajes de correo electrónico, añadir eventos de iCalendar a los correos electrónicos, recibir correos electrónicos y mucho más.
## **Aspose.Email Pop3**
[Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client) implementa el Protocolo de oficina de correos v3 (POP3) en Java. Permite a los desarrolladores de Java añadir funciones de consulta y recepción de correo electrónico a sus aplicaciones Java sin tener que preocuparse por los detalles del protocolo ni por la complejidad de la programación del correo electrónico y la red. Aspose.Email Pop3 admite todos los comandos definidos en el protocolo POP3 estándar y proporciona interfaces fáciles de usar junto con un modelo de objetos compacto e intuitivo. Reduce considerablemente la curva de aprendizaje habitual para los desarrolladores de Java.
### **Pop3: Características principales**
Como parte de Aspose.Email, Aspose.Email Pop3 está diseñado específicamente para Java y está escrito en código Java administrado. Te permite:

- Conéctese a servidores POP3 e inicie sesión en ellos.
- Soporta APOP.
- Mensajes de consulta.
- Recupera mensajes.
- Totalmente compatible con el estilo de programación asíncrono.
- Soporta SSL.
### **Escenarios de Pop3 de Aspose.Email**
Los desarrolladores pueden utilizar Aspose.Email Pop3 en muchos escenarios diferentes. Aquí compartimos un par.
### **Automatización del correo electrónico empresarial**
Aspose.Email Pop3 se puede usar para consultar las bandejas de entrada de correo electrónico y buscar mensajes de correo electrónico. Funciona sin problemas con el componente de envío de correo electrónico, Aspose.Email Mail. Aspose.Email es totalmente compatible con la automatización del correo electrónico. Envía mensajes de correo electrónico con Aspose.Email Mail y recupera mensajes con Aspose.Email Pop3. A continuación, Mime de correo electrónico Aspose. puede analizar los mensajes de correo electrónico descargados.
### **Clientes de correo electrónico**
Aspose.Email Pop3 se puede usar en aplicaciones de clientes de correo electrónico para recibir correos electrónicos.
### **Pop3: Ejemplo de aplicación**
Aquí, demostraremos cómo usar [Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client). Esta clase tiene muchas funciones, pero nos concentraremos en cómo conectarnos a un servidor POP3 y recuperar mensajes. El ejemplo muestra cómo crear una aplicación, así como los ejemplos de código que hacen que la aplicación funcione. Siga los pasos que se indican a continuación para crear una aplicación de ejemplo con Aspose.Email Pop3.

1. Crea una instancia de Pop3Client.
1. Establezca el nombre de host POP3, el inicio de sesión y la contraseña en esta instancia.
1. Crea una instancia de MailMessage y recupera en ella el primer correo electrónico de tu cuenta llamando a la función fetchMessage (). Esto lleva el primer mensaje de tu cuenta de correo electrónico a la instancia de MailMessage.
1. Usa las propiedades From, Subject y HTMLBody de la instancia MailMessage para ver el remitente, el asunto y el cuerpo del mensaje.

Los pasos anteriores se muestran en los ejemplos de código que aparecen a continuación.



~~~Java
// Create a POP3 client
Pop3Client client = new Pop3Client();

// Basic settings (required)
client.setHost("pop3.youdomain.com");
client.setUsername("username");
client.setPassword("psw");

try {
    // Retrieve first message in MailMessage format directly
    MailMessage msg;
    msg = client.fetchMessage(1);
    System.out.println(msg.getFrom().toString());
    System.out.println(msg.getSubject());
    System.out.println(msg.getHtmlBody());
} catch (Exception ex) {
    System.err.println(ex);
}
~~~



Para los servidores habilitados para SSL, necesitamos cambiar las siguientes propiedades del objeto Pop3Client:



~~~Java
// Set implicit security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Mapa de IMAP de Aspose.Email**
[Mapa de IMAP de Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/imapclient) implementa el Protocolo de acceso a mensajes de Internet (IMAP) en Java. Mapa de IMAP de Aspose.Email permite a los desarrolladores de Java añadir capacidades IMAP a sus aplicaciones Java rápidamente, sin tener que entender los detalles del protocolo. El componente permite buscar y cargar mensajes, comprobar el estado de los mensajes nuevos, leídos o no leídos, etc.
### **Imap: Características principales**
Mapa de IMAP de Aspose.Email le permite:

- Busca mensajes de correo electrónico.
- Sube mensajes de correo electrónico.
- Enumera los mensajes de correo electrónico en diferentes carpetas.
- Comprueba el estado de los mensajes de correo electrónico.
- Trabaja con MailMessage.
- Trabaja con soporte SSL.
### **Uso de Mapa de IMAP de Aspose.Email**
Mapa de IMAP de Aspose.Email implementa el Protocolo de acceso a mensajes de Internet en Java. Con él, los desarrolladores pueden consultar y administrar fácilmente los correos electrónicos del servidor IMAP y crear, eliminar o cambiar el nombre de las carpetas de correo electrónico. Con Mapa de IMAP de Aspose.Email, los desarrolladores pueden aprovechar el protocolo IMAP con API fáciles de usar. Pueden acceder a los correos electrónicos desde cualquier PC, ya que los correos electrónicos permanecen guardados en el servidor. Con Mapa de IMAP de Aspose.Email, los desarrolladores pueden crear aplicaciones web o de escritorio que reciban y manipulen correos electrónicos de servidores IMAP. Aspose implementó el protocolo IMAP de acuerdo con los estándares RFC y de autenticación de Internet. Por lo tanto, Mapa de IMAP de Aspose.Email es una implementación segura y con todas las funciones del protocolo IMAP con un modelo de objetos e interfaces fáciles de entender.
### **Imap: Ejemplo de aplicación**
En este artículo se explica cómo usar [Mapa de IMAP de Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/imapclient). Creamos una pequeña aplicación que obtiene la cantidad de mensajes de correo electrónico en su cuenta de correo electrónico IMAP. Siga los pasos que se indican a continuación para crear una aplicación de ejemplo con Mapa de IMAP de Aspose.Email.

1. Crea una instancia de IMAPClient pasando el nombre, el nombre de usuario y la contraseña del servidor IMAP.
1. Llama a la función selectFolder () de la instancia de IMAPClient para seleccionar la carpeta en la que quieres contar el número de mensajes.
1. Ahora llame a la propiedad currentFolder.totalMessageCount de la instancia de IMAPClient para obtener el recuento de mensajes de correo electrónico.
### **Imap: Ejemplos de código**
Los ejemplos de código que aparecen a continuación muestran cómo implementar los pasos descritos anteriormente con Aspose.Email.



~~~Java
// Creates an instance of the class ImapClient by specified the host, username and password
ImapClient client = new ImapClient("localhost", "username", "password");

try {
    client.selectFolder(ImapFolderInfo.IN_BOX);
    String strTemp;
    strTemp = "You have " + client.getCurrentFolder().getTotalMessageCount() + " messages in your account.";
    // Gets number of messages in the folder, Disconnects to imap server.
    System.out.println(strTemp);
} catch (Exception ex) {
    System.err.println(ex);
}
~~~



Para los servidores de correo con SSL activado, defina las siguientes propiedades del objeto IMAPClient:



~~~Java
// Set security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Intercambio de correo electrónico Aspose.Email**
[Intercambio de correo electrónico Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) permite a los desarrolladores administrar los correos electrónicos en Microsoft Exchange Server. Con este componente, puede conectarse, enumerar mensajes y descargar correos electrónicos desde el buzón del servidor Exchange sin comprender los detalles del protocolo subyacente. El componente permite enumerar mensajes, enviar correos electrónicos, descargar mensajes y guardarlos en formato eml o msg en su disco local, etc.
### **Exchange: características principales**
Intercambio de correo electrónico Aspose.Email le permite:

- Conéctese a los servidores Microsoft Exchange.
- Enumera los mensajes de correo electrónico de los buzones de Exchange.
- Enumera los mensajes de correo electrónico de diferentes carpetas, por ejemplo, las carpetas Bandeja de entrada, Enviados, Eliminados o Borradores.
- Elimine los mensajes de cualquier carpeta de los servidores Exchange.
### **Uso de Intercambio de correo electrónico Aspose.Email**
Con Intercambio de correo electrónico Aspose.Email, los desarrolladores pueden acceder a los buzones de Exchange Server desde sus aplicaciones Java. Proporciona una API fácil de usar para administrar los correos electrónicos en los servidores Exchange. Los desarrolladores pueden crear aplicaciones web, de escritorio o de consola que administren los correos electrónicos en los buzones de Exchange.
## **Ejemplo de aplicación Intercambio de correo electrónico Aspose.Email**
En este artículo se muestra cómo usar [Intercambio de correo electrónico Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient). Creamos una aplicación de escritorio sencilla que se conecta a un buzón de Exchange Server, obtiene la lista de mensajes de la carpeta Bandeja de entrada y los muestra en el formulario de Windows.
### **Exchange: ejemplos de pasos de solicitud**
Para ejecutar la aplicación correctamente, necesita las credenciales correctas para acceder a Exchange Server. Aquí obtenemos la información de credenciales (URI, nombre de usuario, contraseña y dominio del servidor Exchange) del formulario de Windows. Este es un ejemplo muy básico, por lo que las propiedades del mensaje (asunto, origen y destino) se muestran simplemente en el cuadro de lista.
### **Exchange: ejemplos de código**
Agregue el siguiente código al controlador de pares de clics del **Listar mensajes** button.


~~~Java
// Clear the items in the listbox
lstMessages.clear();

// Create instance of IEWSClient class by giving credentials and Call ListMessages method to list messages info from Inbox
IEWSClient client = EWSClient.getEWSClient("mailboxURI", "Username", "Password", "Domain");
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : msgCollection) {
    String strMsgInfo = "Subject: " + msgInfo.getSubject() + " == From: " + msgInfo.getFrom().toString() + " == To: " + msgInfo.getTo().toString();
    lstMessages.add(strMsgInfo);
}
~~~
### **Intercambio: Salida**
Esta captura de pantalla muestra los mensajes extraídos del servidor Exchange. El método listMessages () devuelve la información básica, como el asunto, el origen y el identificador del mensaje. Para obtener el mensaje completo, llama al método iewsClient.fetchMessage (). (El uso del IewsClient.fetchMessage () se describe en el artículo [Trabajar con el buzón y los mensajes de Exchange](/email/java/working-with-exchange-mailbox-and-messages).)


## **Mime de correo electrónico Aspose.**
Las extensiones multipropósito de correo de Internet (MIME) son un estándar de Internet que amplía el formato del correo electrónico para admitir texto en conjuntos de caracteres distintos de US-ASCII, archivos adjuntos que no sean de texto, cuerpos de mensajes con varias partes e información de encabezados en conjuntos de caracteres que no sean ASCII. Mime de correo electrónico Aspose. implementa el protocolo MIMI en Java. Actúa como un traductor, ya que puede leer un correo electrónico desde un archivo (.eml, etc.) o desde la memoria (cadena). A continuación, analiza el archivo o la cadena de correo electrónico en partes significativas. Si quieres revisar un archivo de correo electrónico sin tener que preocuparte por los detalles del protocolo MIME (por ejemplo, para extraer un archivo adjunto de un correo electrónico), usa Mime de correo electrónico Aspose..
### **Características principales**
Mime de correo electrónico Aspose. funciona perfectamente con Aspose.Email Pop3 y Aspose.Email Mail.

- Aspose.Email Pop3 recupera los mensajes de correo electrónico de un buzón específico.
- Aspose.Email Mail envía mensajes de correo electrónico a un buzón específico.
- Mime de correo electrónico Aspose. es la bisagra de los dos anteriores y analiza los mensajes de correo electrónico.
