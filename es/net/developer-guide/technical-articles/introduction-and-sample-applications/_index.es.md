---
title: "Introducción y Aplicaciones de Ejemplo"
url: /es/net/introduccion-y-aplicaciones-de-ejemplo/
weight: 260
type: docs
---


## **Escenarios de Uso de Aspose.Email.Mail**
Este artículo sugiere una serie de usos posibles para Aspose.Email para .NET, centrándose en particular en las características de programación de correo electrónico del componente.
### **Software de Boletines Informativos**
La API de [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) se puede utilizar para crear una aplicación robusta de boletines informativos. Utilizando el soporte de Aspose.Email para agregar objetos incrustados (como imágenes, sonidos, etc.), es posible crear boletines informativos en HTML ricos, completos con imágenes (y otros objetos incrustados). Usando la función de correo masivo de la API de Aspose.Email.Mail, también es posible enviar enormes correos masivos en un período de tiempo limitado. Aspose.Email.Mail también proporciona una función de combinación de correspondencia basada en plantillas que se puede utilizar para crear una plantilla de boletín informativo. La plantilla del boletín informativo se puede utilizar para realizar una combinación de correspondencia para enviar boletines informativos masivos. Hay muchas otras tareas posibles que Aspose.Email.Mail puede realizar en una aplicación de marketing por correo electrónico.
### **Otras Herramientas de Marketing**
Similar a las aplicaciones de boletines informativos, se pueden construir muchos otros tipos de software utilizando Aspose.Email.Mail. Úselo para construir marketing por correo electrónico, correo masivo y correo masivo de campañas electrónicas, y más.
### **Aplicaciones Empresariales**
Aspose.Email.Mail se puede utilizar en casi todos los tipos de aplicaciones empresariales para realizar tareas utilitarias:

- Alertas por correo electrónico: Enviar alertas por correo electrónico para informar a los usuarios sobre actividades.
- Solicitudes de reuniones: Enviar solicitudes de reuniones de negocios utilizando el soporte de iCalendar de Aspose.Email.Mail.
- Informes programados por correo electrónico: Los informes son fundamentales en la mayoría de las aplicaciones empresariales. Muchos informes de negocios se generan a intervalos. Use Aspose.Email.Mail para enviar informes programados por correo electrónico.
### **Clientes de Correo Electrónico**
Aspose.Email.Mail también se puede utilizar en clientes de correo electrónico para enviar correos electrónicos normales. Soporta adjuntos, objetos incrustados, eventos de iCalendar, combinaciones de correspondencia, envío de correos masivos, y más, por lo que Aspose.Email.Mail es la mejor opción para crear aplicaciones de cliente de correo electrónico basadas en Windows o la web.
## **Aplicación de Ejemplo de Aspose.Email.Mail**
Para ilustrar cómo usar Aspose.Email.Mail, crearemos una aplicación llamada 'Mi Primer Correo' que demuestra cómo construir un mensaje de correo electrónico con la [clase MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) y luego enviarlo utilizando la clase SmtpClient.
### **Correo: Pasos de la Aplicación de Ejemplo**
Siga los pasos a continuación para crear la aplicación 'Mi Primer Correo' utilizando Aspose.Email.

1. Abra Visual Studio.
1. En el menú **Archivo**, seleccione **Nuevo**, luego **Proyecto**. (Elija crear una aplicación de Windows en C# o VB.NET).
1. Si tiene una licencia, aplíquela para usar la versión completa de Aspose.Email.
1. Importe el DLL de Aspose.Email en la aplicación haciendo clic derecho en **Referencia** en el Explorador de soluciones.
1. Diseñe su aplicación de Windows: cree una interfaz que lleve tres campos: **De**, **Para** y **Mensaje**.
1. Haga doble clic en el botón **Enviar** en la vista de diseño y escriba su código en el editor.
1. Cree una instancia de la clase MailMessage y use sus propiedades para construir un mensaje de correo electrónico. (Se utilizan instancias de la clase MailMessage para construir mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante la clase SmtpClient).
1. Cree una instancia de la clase SmtpClient y use sus propiedades para enviar un mensaje de correo electrónico.
1. Pruebe su aplicación de Windows presionando F5.
1. Escriba direcciones en los campos **De** y **Para**.
1. Escriba un mensaje en el campo **Cuerpo del Mensaje**.
1. Haga clic en **Enviar**.

Los pasos anteriores se describen a continuación, haga doble clic en el botón **Enviar** en la vista de diseño y agregue el siguiente código:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-AsposeEmailMail.cs" >}}



Al conectarse a un servidor habilitado para SSL, necesitamos establecer las siguientes propiedades del objeto SMTPClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-SSLEnabledSMTP.cs" >}}
### **Conclusión**
[Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) es un componente muy poderoso con el que los desarrolladores pueden realizar casi todas las tareas de correo electrónico, como enviar correos masivos multihilo, utilizar combinación de correspondencia, agregar archivos adjuntos, incrustar imágenes y sonidos en mensajes de correo electrónico, agregar eventos de iCalendar a correos electrónicos, recibir correos electrónicos y mucho más.
## **Aspose.Email.Pop3**
[Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) implementa el Protocolo de Oficina de Correos v3 (POP3) en el marco .NET. Permite a los desarrolladores de .NET agregar características de consulta y recepción de correos electrónicos a sus aplicaciones .NET sin involucrarse en los detalles del protocolo y la complejidad de la programación de correos electrónicos y redes. Aspose.Email.Pop3 soporta todos los comandos definidos en el protocolo estándar POP3 y proporciona interfaces fáciles de usar junto con un modelo de objeto compacto e intuitivo. Reduce en gran medida la curva de aprendizaje habitual para los desarrolladores de .NET.
### **Pop3: Principales Características**
Como parte de Aspose.Email, Aspose.Email.Pop3 está diseñado específicamente para .NET y está escrito en código C# administrado. Permite:

- Conectar e iniciar sesión en servidores POP3.
- Soportar APOP.
- Consultar mensajes.
- Recuperar mensajes.
- Soporte completo para el estilo de programación asíncrona.
- Soporta SSL.
### **Escenarios de Aspose.Email.Pop3**
Aspose.Email.Pop3 puede ser utilizado por desarrolladores en muchos escenarios diferentes. Aquí, compartimos un par.
### **Automatización de Correo Electrónico Empresarial**
Aspose.Email.Pop3 se puede utilizar para consultar bandejas de entrada de correo electrónico y obtener mensajes de correo electrónico. Funciona sin problemas con el componente de envío de correo electrónico, Aspose.Email.Mail. Aspose.Email apoya completamente la automatización del correo electrónico. Envíe mensajes de correo electrónico con Aspose.Email.Mail y obtenga mensajes con Aspose.Email.Pop3. Los mensajes de correo electrónico descargados pueden ser analizados por Aspose.Email.Mime.
### **Clientes de Correo Electrónico**
Aspose.Email.Pop3 se puede utilizar en aplicaciones de cliente de correo electrónico para recibir correos electrónicos.
### **Pop3: Aplicación de Ejemplo**
Aquí, demostraremos cómo usar [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client). Esta clase tiene muchas características, pero nos concentraremos en cómo conectarnos a un servidor POP3 y recuperar mensajes. El ejemplo muestra cómo crear una aplicación en Visual Studio, así como los ejemplos de código que hacen que la aplicación funcione. Siga los pasos a continuación para crear una aplicación de ejemplo utilizando Aspose.Email.Pop3.

1. Abra Visual Studio.
1. En el menú **Archivo**, seleccione **Nuevo** y luego **Proyecto**.
1. Elija una aplicación de Windows en C# o VB.NET.
1. Importe el Aspose.Email.dll en la aplicación haciendo clic derecho en **Referencia** en el Explorador de soluciones.
1. Ahora diseñe una aplicación de Windows como se muestra a continuación.
1. Cree una instancia de Pop3Client.
1. Establezca el nombre de host POP3, nombre de usuario y contraseña en esta instancia.
1. Llame a las funciones Connect() y Login() de Pop3Client.
1. Cree una instancia de MailMessage y obtenga el primer correo electrónico en su cuenta en ella llamando a la función FetchMessage(). Esto lleva el primer mensaje de su cuenta de correo electrónico a la instancia de MailMessage.
1. Utilice las propiedades From, Subject y HtmlBody de la instancia de MailMessage para ver el remitente, el asunto y el cuerpo del mensaje.

Los pasos anteriores se demuestran en los ejemplos de código a continuación. Use el siguiente código detrás de cualquier botón o en el evento OnLoad de un formulario.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-AsposeEmailPop3.cs" >}}



Para servidores habilitados para SSL, necesitamos cambiar las siguientes propiedades del objeto Pop3Client:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Imap**
[Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap) implementa el Protocolo de Acceso a Mensajes de Internet (IMAP) en los marcos de .NET. Aspose.Email.Imap permite a los desarrolladores de .NET agregar capacidades IMAP a sus aplicaciones .NET rápidamente, sin tener que entender los detalles del protocolo. El componente soporta la recuperación y carga de mensajes, la comprobación del estado de mensajes nuevos/leídos/no leídos, y más.
### **Imap: Principales Características**
Aspose.Email.Imap le permite:

- Recuperar mensajes de correo electrónico.
- Cargar mensajes de correo electrónico.
- Listar mensajes de correo electrónico en diferentes carpetas.
- Verificar el estado de los mensajes de correo electrónico.
- Trabajar con MailMessage.
- Trabajar con soporte SSL.
### **Uso de Aspose.Email.Imap**
Aspose.Email.Imap implementa el Protocolo de Acceso a Mensajes de Internet en los marcos de .NET. Con él, los desarrolladores pueden consultar y gestionar correos electrónicos de servidores IMAP fácilmente, y crear, eliminar o renombrar carpetas de correo electrónico. Usando Aspose.Email.Imap, los desarrolladores pueden aprovechar el protocolo IMAP con APIs fáciles de usar. Pueden acceder a correos electrónicos desde cualquier PC ya que los correos electrónicos permanecen guardados en el servidor. Usando Aspose.Email.Imap, los desarrolladores pueden crear aplicaciones web o de escritorio que reciban y manipulen correos electrónicos de servidores IMAP. Aspose implementó el protocolo IMAP de acuerdo con los estándares de autenticación de internet y RFC. Por lo tanto, Aspose.Email.Imap es una implementación segura y con todas las características del protocolo IMAP con un modelo de objeto e interfaces fáciles de entender.
### **Imap: Aplicación de Ejemplo**
Este artículo explica cómo usar [Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap). Creamos una pequeña aplicación que obtiene el número de mensajes de correo electrónico en su cuenta de correo IMAP. Siga los pasos a continuación para crear una aplicación de ejemplo utilizando Aspose.Email.Imap.

1. Abra Visual Studio.
1. En el menú **Archivo**, seleccione **Nuevo** y luego **Proyecto**.
1. Elija una aplicación de Windows en C# o VB.NET.
1. Importe el Aspose.Email.dll en esta aplicación haciendo clic derecho en **Referencia** en el Explorador de soluciones.
1. Cree una instancia de ImapClient pasando el nombre del servidor IMAP, nombre de usuario y contraseña.
1. Llame a la función Connect() de la instancia de ImapClient para conectarse al servidor.
1. Llame a la función SelectFolder() de la instancia de ImapClient para seleccionar la carpeta en la que desea contar el número de mensajes.
1. Ahora llame a la propiedad TotalMessageCount de CurrentFolder de la instancia de ImapClient para obtener el recuento de mensajes de correo electrónico.
### **Imap: Ejemplos de Código**
Los ejemplos de código a continuación van detrás del botón o en el evento OnLoad en un formulario. Muestran cómo implementar los pasos descritos anteriormente con Aspose.Email.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-AsposeEmailIMAP.cs" >}}



Para servidores de correo habilitados para SSL, establezca las siguientes propiedades del objeto ImapClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Exchange**
[Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index) permite a los desarrolladores gestionar correos electrónicos en Microsoft Exchange Server. Usando este componente puede conectarse, listar mensajes y descargar correos electrónicos de la bandeja de entrada del servidor Exchange sin comprender los detalles del protocolo subyacente. El componente soporta listar mensajes, enviar correos electrónicos, descargar mensajes y guardarlos en formato eml o msg en su disco local, etc.
### **Exchange: Principales Características**
Aspose.Email.Exchange le permite:

- Conectarse a Servidores Microsoft Exchange.
- Listar mensajes de correo electrónico en bandejas de entrada de Exchange.
- Listar mensajes de correo electrónico de diferentes carpetas, por ejemplo, la bandeja de entrada, enviados, eliminados o borradores.
- Eliminar mensajes en cualquier carpeta de los Servidores Exchange.
### **Uso de Aspose.Email.Exchange**
Con Aspose.Email.Exchange, los desarrolladores pueden acceder a las bandejas de entrada de Exchange Server desde sus aplicaciones .NET. Proporciona una API fácil de usar para gestionar correos electrónicos en los Servidores Exchange. Los desarrolladores pueden crear aplicaciones de consola, escritorio o web que gestionen correos electrónicos en bandejas de entrada de Exchange.
## **Aplicación de Ejemplo de Aspose.Email.Exchange**
Este artículo demuestra cómo usar [Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index). Creamos una aplicación de escritorio simple que se conecta a la bandeja de entrada de un servidor Exchange, obtiene la lista de mensajes en la carpeta de la bandeja de entrada y los muestra en el formulario de Windows.
### **Exchange: Pasos de la Aplicación de Ejemplo**
1. Abra Microsoft Visual Studio.
1. Cree un nuevo proyecto. (Seleccione el idioma de su elección C# o VB.NET)
1. Agregue una referencia al Aspose.Email.dll en su proyecto haciendo clic derecho en el proyecto y seleccionando **Agregar Referencia** en el menú.
1. Diseñe un formulario de Windows como el que se muestra a continuación:

Para ejecutar la aplicación con éxito, necesita las credenciales correctas para acceder al Servidor Exchange. Aquí, obtenemos la información de credenciales - URI del Servidor Exchange, nombre de usuario, contraseña y dominio - del formulario de Windows. Este es un ejemplo muy básico, por lo que las propiedades del mensaje - asunto, de y para - se muestran simplemente en la lista.
### **Exchange: Ejemplos de Código**
Agregue el siguiente código en el controlador de eventos de clic del botón **Listar Mensajes**.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailExchangeSampleApp-AsposeEmailExchange.cs" >}}
### **Exchange: Salida**
Esta captura de pantalla muestra los mensajes recuperados del Servidor Exchange. El método ListMessages() devuelve la información básica como asunto, de, para e ID del mensaje. Para obtener el mensaje completo, llame al método ExchangeClient.SaveMessage(). (El uso de ExchangeClient.SaveMessage() se describe en el artículo [Guardando Mensajes desde la Bandeja de Entrada del Servidor Exchange en Formato EML y MSG](/email/net/working-with-exchange-mailbox-and-messages/#saving-messages).)

|![todo:image_alt_text](introduction-and-sample-applications_1.png)|
| :- |
## **Aspose.Email.Mime**
Las Extensiones de Correo de Internet Multipropósito (MIME) son un estándar de Internet que extiende el formato de correo electrónico para soportar texto en conjuntos de caracteres distintos de US-ASCII, archivos adjuntos no textuales, cuerpos de mensajes de múltiples partes y información de encabezado en conjuntos de caracteres no ASCII. Aspose.Email.Mime implementa el protocolo MIMI en marcos de .NET. Actúa como un traductor ya que puede leer un correo electrónico desde un archivo (.eml, etc.) o desde memoria (cadena). Luego analiza el archivo o la cadena de correo electrónico en partes significativas. Si desea explorar un archivo de correo electrónico sin involucrarse con los detalles del protocolo MIME, por ejemplo, para extraer un archivo adjunto de un correo electrónico, use Aspose.Email.Mime.
### **Características Principales**
Aspose.Email.Mime funciona perfectamente con Aspose.Email.Pop3 y Aspose.Email.Mail.

- [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) recupera mensajes de correo electrónico de una bandeja de entrada especificada.
- [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) envía mensajes de correo electrónico a una bandeja de entrada especificada.
- [Aspose.Email.Mime](https://apireference.aspose.com/email/net/aspose.email.mime) es el eje de los anteriores y analiza mensajes de correo electrónico.