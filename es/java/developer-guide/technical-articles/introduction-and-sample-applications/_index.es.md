---
title: "Introducción y Aplicaciones de Ejemplo"
url: /es/java/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Escenarios de Uso de Aspose.Email Mail**
Este artículo sugiere una serie de posibles usos para Aspose.Email para Java, centrándose en particular en las características de programación de correo electrónico del componente.
### **Software de Boletines**
La API de Aspose.Email Mail se puede utilizar para crear una aplicación robusta de boletines. Usando el soporte de Aspose.Email para agregar objetos incrustados (como imágenes, sonidos, etc.), es posible crear boletines HTML ricos completos con imágenes (y otros objetos incrustados). Usando la función de correo masivo de la API de Aspose.Email Mail, también es posible enviar grandes correos electrónicos masivos en un período de tiempo limitado. Aspose.Email Mail también proporciona una función de combinación de correspondencia basada en plantillas que se puede utilizar para crear una plantilla de boletín. La plantilla del boletín se puede utilizar para realizar una combinación de correspondencia para enviar un boletín masivo. Hay muchas otras tareas posibles que Aspose.Email Mail puede realizar en una aplicación de marketing por correo electrónico.
### **Otras Herramientas de Marketing**
Al igual que con las aplicaciones de boletines, se pueden construir muchos otros tipos de software utilizando Aspose.Email Mail. Úselo para construir marketing por correo electrónico, correo masivo y correo masivo de campañas electrónicas, y más.
### **Aplicaciones Empresariales**
Aspose.Email Mail se puede utilizar en casi todos los tipos de aplicaciones empresariales para realizar tareas utilitarias:

- Alertas por correo electrónico: Enviar alertas por correo electrónico para informar a los usuarios sobre actividades.
- Solicitudes de reunión: Enviar solicitudes de reunión empresarial utilizando el soporte iCalendar de Aspose.Email Mail.
- Informes programados por correo electrónico: Los informes son parte integral de la mayoría de las aplicaciones empresariales. Muchos informes empresariales se generan a intervalos. Use Aspose.Email Mail para enviar informes programados por correo electrónico.
### **Clientes de Correo Electrónico**
Aspose.Email Mail también se puede utilizar en clientes de correo electrónico para enviar correos electrónicos normales. Soporta adjuntos, objetos incrustados, eventos de iCalendar, combinaciones de correo, envío de correos electrónicos masivos, y más, por lo que Aspose.Email Mail es la mejor opción para crear aplicaciones de clientes de correo electrónico.
## **Aplicación de Ejemplo de Aspose.Email Mail**
Para ilustrar cómo usar Aspose.Email Mail, crearemos una aplicación que demuestre cómo construir un mensaje de correo electrónico con la [clase MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) y luego enviarlo usando la clase SmtpClient.
### **Correo: Pasos de la Aplicación de Ejemplo**
Siga los pasos a continuación para crear una aplicación usando Aspose.Email.

1. Diseñe su aplicación: cree una interfaz que tenga tres campos: **De**, **A** y **Mensaje**.
1. Haga doble clic en el botón **Enviar** en la vista de diseño y escriba su código en el editor.
1. Cree una instancia de la clase MailMessage y use sus propiedades para construir un mensaje de correo electrónico. (Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega utilizando la clase SmtpClient).
1. Cree una instancia de la clase SmtpClient y use sus propiedades para enviar un mensaje de correo electrónico.
1. Pruebe su Aplicación.
1. Escriba direcciones en los campos **De** y **A**.
1. Escriba un mensaje en el campo **Cuerpo del Mensaje**.
1. Haga clic en **Enviar**.

Los pasos anteriores se describen a continuación como: haga doble clic en el botón **Enviar** en la vista de diseño y agregue el siguiente código:



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
System.out.println("Mensaje Enviado");
~~~


Al conectarse a un servidor habilitado para SSL, necesitamos establecer las siguientes propiedades del objeto SMTPClient



~~~Java
// Set the port to 587. This is the SSL port of Gmail SMTP server, set the security mode to explicit
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~
### **Conclusión**
Aspose.Email Mail es un componente muy poderoso con el que los desarrolladores pueden realizar casi todas las tareas de correo electrónico, como enviar correos electrónicos masivos en múltiples hilos, usar combinación de correspondencia, agregar archivos adjuntos, incrustar imágenes y sonidos en mensajes de correo electrónico, agregar eventos de iCalendar a correos electrónicos, recibir correos electrónicos y mucho más.
## **Aspose.Email Pop3**
[Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client) implementa el Protocolo de Oficina de Correos v3 (POP3) en Java. Permite a los desarrolladores de Java agregar características de consulta y recepción de correo electrónico a sus aplicaciones Java sin involucrarse en los detalles del protocolo y la complejidad de la programación de correo electrónico y redes. Aspose.Email Pop3 admite todos los comandos definidos en el protocolo estándar POP3 y proporciona interfaces fáciles de usar junto con un modelo de objeto compacto e intuitivo. Reduce considerablemente la curva de aprendizaje habitual para los desarrolladores de Java.
### **Pop3: Características Principales**
Como parte de Aspose.Email, Aspose.Email Pop3 está diseñado específicamente para Java y está escrito en código Java administrado. Permite:

- Conectar y acceder a servidores POP3.
- Soporte APOP.
- Consultar mensajes.
- Recuperar mensajes.
- Soporte completo para el estilo de programación asíncrono.
- Soporte SSL.
### **Escenarios de Aspose.Email Pop3**
Aspose.Email Pop3 puede ser utilizado por desarrolladores en muchos escenarios diferentes. Aquí, compartimos un par.
### **Automatización de Correo Electrónico Empresarial**
Aspose.Email Pop3 puede ser utilizado para consultar bandejas de entrada de correos electrónicos y recuperar mensajes de correo electrónico. Funciona sin problemas con el componente de envío de correos electrónicos, Aspose.Email Mail. Aspose.Email admite completamente la automatización del correo electrónico. Envíe mensajes de correo electrónico con Aspose.Email Mail y recupere mensajes con Aspose.Email Pop3. Los mensajes de correo electrónico descargados pueden ser analizados por Aspose.Email Mime.
### **Clientes de Correo Electrónico**
Aspose.Email Pop3 puede usarse en aplicaciones de clientes de correo electrónico para recibir correos electrónicos.
### **Pop3: Aplicación de Ejemplo**
Aquí, demostraremos cómo usar [Aspose.Email Pop3](https://apireference.aspose.com/email/java/com.aspose.email/pop3client). Esta clase tiene muchas características, pero nos concentraremos en cómo conectarnos a un servidor POP3 y recuperar mensajes. El ejemplo muestra cómo crear una aplicación así como los ejemplos de código que hacen funcionar la aplicación. Siga los pasos dados a continuación para crear una aplicación de ejemplo utilizando Aspose.Email Pop3.

1. Cree una instancia de Pop3Client.
1. Establezca el nombre del servidor POP3, el inicio de sesión y la contraseña en esta instancia.
1. Cree una instancia de MailMessage y recupere el primer correo electrónico en su cuenta en ella llamando a la función fetchMessage(). Esto trae el primer mensaje de su cuenta de correo electrónico a la instancia de MailMessage.
1. Use las propiedades From, Subject y HtmlBody de la instancia de MailMessage para ver el remitente, el asunto y el cuerpo del mensaje.

Los pasos anteriores se demuestran en los siguientes ejemplos de código.



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



Para servidores habilitados para SSL, necesitamos cambiar las siguientes propiedades del objeto Pop3Client:



~~~Java
// Set implicit security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Aspose.Email Imap**
[Aspose.Email Imap](https://apireference.aspose.com/email/java/com.aspose.email/imapclient) implementa el Protocolo de Acceso a Mensajes por Internet (IMAP) en Java. Aspose.Email Imap permite a los desarrolladores de Java agregar capacidades IMAP a sus aplicaciones Java rápidamente, sin tener que entender los detalles del protocolo. El componente admite la recuperación y carga de mensajes, la verificación de estado de nuevos/leídos/no leídos de los mensajes, etc.
### **Imap: Características Principales**
Aspose.Email Imap permite:

- Recuperar mensajes de correo electrónico.
- Cargar mensajes de correo electrónico.
- Listar mensajes de correo electrónico en diferentes carpetas.
- Comprobar el estado de los mensajes de correo electrónico.
- Trabajar con MailMessage.
- Trabajar con soporte SSL.
### **Uso de Aspose.Email Imap**
Aspose.Email Imap implementa el Protocolo de Acceso a Mensajes por Internet en Java. Con él, los desarrolladores pueden consultar y administrar correos electrónicos en servidores IMAP, y crear, eliminar o renombrar carpetas de correo electrónico. Utilizando Aspose.Email Imap, los desarrolladores pueden aprovechar el protocolo IMAP con APIs fáciles de usar. Pueden acceder a los correos electrónicos desde cualquier PC ya que los correos electrónicos permanecen guardados en el servidor. Usando Aspose.Email Imap, los desarrolladores pueden crear aplicaciones web o de escritorio que reciban y manipulen correos electrónicos desde servidores IMAP. Aspose implementó el protocolo IMAP de acuerdo con la autenticación de internet y los estándares RFC. Por lo tanto, Aspose.Email Imap es una implementación segura y totalmente funcional del protocolo IMAP con un modelo de objeto y interfaces fáciles de entender.
### **Imap: Aplicación de Ejemplo**
Este artículo explica cómo usar [Aspose.Email Imap](https://apireference.aspose.com/email/java/com.aspose.email/imapclient). Creamos una pequeña aplicación que obtiene el número de mensajes de correo electrónico en su cuenta de correo IMAP. Siga los pasos dados a continuación para crear una aplicación de ejemplo utilizando Aspose.Email Imap.

1. Cree una instancia de ImapClient pasando el nombre del servidor IMAP, el inicio de sesión y la contraseña.
1. Llame a la función selectFolder() de la instancia de ImapClient para seleccionar la carpeta de la que desea contar el número de mensajes.
1. Ahora llame a la propiedad TotalMessageCount de CurrentFolder de la instancia de ImapClient para obtener el número de mensajes de correo electrónico.
### **Imap: Ejemplos de Código**
Los ejemplos de código a continuación muestran cómo implementar los pasos descritos anteriormente con Aspose.Email.



~~~Java
// Creates an instance of the class ImapClient by specified the host, username and password
ImapClient client = new ImapClient("localhost", "username", "password");

try {
    client.selectFolder(ImapFolderInfo.IN_BOX);
    String strTemp;
    strTemp = "Tienes " + client.getCurrentFolder().getTotalMessageCount() + " mensajes en tu cuenta.";
    // Gets number of messages in the folder, Disconnects to imap server.
    System.out.println(strTemp);
} catch (Exception ex) {
    System.err.println(ex);
}
~~~



Para servidores de correo habilitados para SSL, establezca las siguientes propiedades del objeto ImapClient:



~~~Java
// Set security mode
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~
## **Aspose.Email Exchange**
[Aspose.Email Exchange](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) permite a los desarrolladores gestionar correos electrónicos en Microsoft Exchange Server. Usando este componente puedes conectarte, listar mensajes y descargar correos electrónicos del buzón del servidor de Exchange sin comprender los detalles del protocolo subyacente. El componente admite listar mensajes, enviar correos electrónicos, descargar mensajes y guardar en formato eml o msg en su disco local, etc.
### **Exchange: Características Principales**
Aspose.Email Exchange le permite:

- Conectar a Microsoft Exchange Servers.
- Listar mensajes de correo electrónico en los buzones de Exchange.
- Listar mensajes de correo electrónico desde diferentes carpetas, por ejemplo, la Bandeja de entrada, Enviados, Eliminados o Borradores.
- Eliminar mensajes en cualquier carpeta en los Servidores de Exchange.
### **Uso de Aspose.Email Exchange**
Con Aspose.Email Exchange, los desarrolladores pueden acceder a los buzones del servidor de Exchange desde sus aplicaciones Java. Proporciona una API fácil de usar para gestionar correos electrónicos en los Servidores de Exchange. Los desarrolladores pueden crear aplicaciones de consola, de escritorio o web que gestionen correos electrónicos en buzones de Exchange.
## **Aplicación de Ejemplo de Aspose.Email Exchange**
Este artículo demuestra cómo usar [Aspose.Email Exchange](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient). Creamos una simple aplicación de escritorio que se conecta a un buzón del Servidor de Exchange, obtiene la lista de mensajes en la carpeta de la Bandeja de entrada y los muestra en el formulario de Windows.
### **Exchange: Pasos de la Aplicación de Ejemplo**
Para ejecutar la aplicación correctamente, necesita las credenciales adecuadas para acceder al Servidor de Exchange. Aquí, obtenemos la información de credenciales - URI del Servidor de Exchange, nombre de usuario, contraseña y dominio - del formulario de Windows. Este es un ejemplo muy básico, por lo que las propiedades del mensaje - asunto, de y para - se muestran simplemente en el cuadro de lista.
### **Exchange: Ejemplos de Código**
Agregue el siguiente código en el controlador de eventos clic del botón **Listar Mensajes**.


~~~Java
// Clear the items in the listbox
lstMessages.clear();

// Create instance of IEWSClient class by giving credentials and Call ListMessages method to list messages info from Inbox
IEWSClient client = EWSClient.getEWSClient("mailboxURI", "Username", "Password", "Domain");
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : msgCollection) {
    String strMsgInfo = "Asunto: " + msgInfo.getSubject() + " == De: " + msgInfo.getFrom().toString() + " == Para: " + msgInfo.getTo().toString();
    lstMessages.add(strMsgInfo);
}
~~~
### **Exchange: Salida**
Esta captura de pantalla muestra los mensajes extraídos del Servidor de Exchange. El método listMessages() devuelve la información básica como asunto, de, para e ID del mensaje. Para obtener el mensaje completo, llame al método IEWSClient.fetchMessage(). (El uso de IEWSClient.fetchMessage() se describe en el artículo [Trabajando con Buzón de Exchange y Mensajes](/email/java/working-with-exchange-mailbox-and-messages).)


## **Aspose.Email Mime**
Extensiones de Correo de Internet Multipropósito (MIME) es un estándar de Internet que extiende el formato de correo electrónico para admitir texto en conjuntos de caracteres distintos de US-ASCII, archivos adjuntos no de texto, cuerpos de mensajes de varias partes e información de encabezado en conjuntos de caracteres no ASCII. Aspose.Email Mime implementa el protocolo MIMI en Java. Actúa como un traductor, ya que puede leer un correo electrónico desde un archivo (.eml, etc.) o desde la memoria (cadena). Luego analiza el archivo o cadena de correo electrónico en partes significativas. Si desea revisar un archivo de correo electrónico sin involucrarse con los detalles del protocolo MIME, por ejemplo, para extraer un archivo adjunto de un correo electrónico, use Aspose.Email Mime.
### **Características Principales**
Aspose.Email Mime funciona perfectamente con Aspose.Email Pop3 y Aspose.Email Mail.

- Aspose.Email Pop3 recupera mensajes de correo electrónico de un buzón específico.
- Aspose.Email Mail envía mensajes de correo electrónico a un buzón específico.
- Aspose.Email Mime es el eje de los dos anteriores y analiza los mensajes de correo electrónico.