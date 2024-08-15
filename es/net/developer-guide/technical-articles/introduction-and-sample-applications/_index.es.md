---
title: "Introducción y ejemplos de aplicaciones"
url: /es/net/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Escenarios de uso de Aspose.Email.Mail**
En este artículo se sugieren varios usos posibles de Aspose.Email para .NET, centrándose en particular en las funciones de programación de correo electrónico del componente.
### **Software para boletines**
The [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) La API se puede utilizar para crear una aplicación sólida de boletines. Con la compatibilidad de Aspose.Email para agregar objetos incrustados (como imágenes, sonidos, etc.), es posible crear boletines HTML enriquecidos con imágenes (y otros objetos incrustados). Con la función de correo masivo de la API Aspose.Email.Mail, también es posible enviar correos masivos de gran tamaño en un período de tiempo limitado. Aspose.Email.Mail también proporciona una función de combinación de correspondencia basada en plantillas que se puede utilizar para crear una plantilla de boletín informativo. La plantilla de boletín se puede usar para realizar una combinación de correspondencia para enviar boletines masivos. Hay muchas otras tareas posibles que Aspose.Email.Mail puede realizar en una aplicación de marketing por correo electrónico.
### **Otras herramientas de marketing**
Al igual que las aplicaciones de boletines informativos, se pueden crear muchos otros tipos de software con Aspose.Email.Mail. Úselo para crear marketing por correo electrónico, correo masivo y correo masivo para campañas electrónicas, y más.
### **Aplicaciones empresariales**
Aspose.Email.Mail se puede usar en casi todo tipo de aplicaciones empresariales para realizar tareas de utilidad:

- Alertas por correo electrónico: envíe alertas por correo electrónico para informar a los usuarios sobre las actividades.
- Solicitudes de reunión: envíe solicitudes de reuniones de negocios mediante el soporte iCalendar de Aspose.Email.Mail.
- Informes programados por correo electrónico: los informes son parte integral de la mayoría de las aplicaciones empresariales. Muchos informes empresariales se generan a intervalos. Utilice Aspose.Email.Mail para enviar por correo electrónico los informes programados.
### **Clientes de correo electrónico**
Aspose.Email.Mail también se puede usar en clientes de correo electrónico para enviar correos electrónicos normales. Admite archivos adjuntos, objetos incrustados, eventos de iCalendar, combinaciones de correspondencia, enviar correos electrónicos masivos, etc., por lo que Aspose.Email.Mail es la mejor opción para crear aplicaciones de cliente de correo electrónico basadas en Windows o basadas en la web.
## **Ejemplo de aplicación Aspose.Email.Mail**
Para ilustrar cómo usar Aspose.Email.Mail, crearemos una aplicación llamada «Mi primer correo electrónico» que muestra cómo crear un mensaje de correo electrónico con el [Clase MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) y luego envíelo usando la clase SmtpClient.
### **Correo: ejemplos de pasos de solicitud**
Siga los pasos que se indican a continuación para crear la aplicación «Mi primer correo» con Aspose.Email.

1. Abra Visual Studio.
1. En el **File** menú, seleccionar **New**, entonces **Project**. (Elija crear una aplicación de Windows en C# o VB.NET).
1. Si tiene una licencia, aplíquela para usar la versión completa de Aspose.Email.
1. Importe la DLL Aspose.Email a la aplicación haciendo clic con el botón derecho **Reference** en el Explorador de soluciones.
1. Diseñe su aplicación para Windows: cree una interfaz que ocupe tres campos: **From**, **To** and **Message**.
1. Haga doble clic en **Send** pulse el botón en la vista de diseño y escriba su código en el editor.
1. Crea una instancia de la clase MailMessage y usa sus propiedades para crear un mensaje de correo electrónico. (Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante la clase SmtpClient).
1. Crea una instancia de la clase SmtpClient y usa sus propiedades para enviar un mensaje de correo electrónico.
1. Pruebe la aplicación de Windows pulsando F5.
1. Escriba las direcciones en **From** and **To** fields.
1. Escriba un mensaje en **Cuerpo del mensaje** field.
1. Click **Send**.

Los pasos anteriores se describen a continuación, haga doble clic en **Send** botón en la vista de diseño y añada el siguiente código:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-AsposeEmailMail.cs" >}}



Al conectarnos a un servidor con SSL habilitado, necesitamos establecer las siguientes propiedades del objeto SMTPClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-SSLEnabledSMTP.cs" >}}
### **Conclusion**
[Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) es un componente muy potente con el que los desarrolladores pueden realizar prácticamente tareas de correo electrónico, como enviar correos electrónicos masivos con varios subprocesos, combinar correspondencia, añadir archivos adjuntos, incrustar imágenes y sonidos en los mensajes de correo electrónico, añadir eventos de iCalendar a los correos electrónicos, recibir correos electrónicos y mucho más.
## **Aspose.Email.Pop3**
[Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) implementa el Protocolo de oficina de correos v3 (POP3) en el.NET Framework. Permite a los desarrolladores de.NET añadir funciones de consulta y recepción de correo electrónico a sus aplicaciones.NET sin tener que preocuparse por los detalles del protocolo ni por la complejidad de la programación del correo electrónico y la red. Aspose.Email.Pop3 admite todos los comandos definidos en el protocolo POP3 estándar y proporciona interfaces fáciles de usar junto con un modelo de objetos compacto e intuitivo. Reduce considerablemente la curva de aprendizaje habitual de los desarrolladores de.NET.
### **Pop3: Características principales**
Como parte de Aspose.Email, Aspose.Email.Pop3 está diseñado específicamente para .NET y está escrito en código C# administrado. Te permite:

- Conéctese a servidores POP3 e inicie sesión en ellos.
- Soporta APOP.
- Mensajes de consulta.
- Recupera mensajes.
- Totalmente compatible con el estilo de programación asíncrono.
- Soporta SSL.
### **Escenarios de Aspose.Email.Pop3**
Los desarrolladores pueden usar Aspose.Email.Pop3 en muchos escenarios diferentes. Aquí compartimos un par.
### **Automatización del correo electrónico empresarial**
Aspose.Email.Pop3 se puede usar para consultar las bandejas de entrada de correo electrónico y obtener mensajes de correo electrónico. Funciona sin problemas con el componente de envío de correo electrónico, Aspose.Email.Mail. Aspose.Email es totalmente compatible con la automatización del correo electrónico. Envía mensajes de correo electrónico con Aspose.Email.Mail y recupera mensajes con Aspose.Email.Pop3. A continuación, Aspose.Email.Mime puede analizar los mensajes de correo electrónico descargados.
### **Clientes de correo electrónico**
Aspose.Email.Pop3 se puede usar en aplicaciones de clientes de correo electrónico para recibir correos electrónicos.
### **Pop3: Ejemplo de aplicación**
Aquí, demostraremos cómo usar [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client). Esta clase tiene muchas funciones, pero nos concentraremos en cómo conectarnos a un servidor POP3 y recuperar mensajes. El ejemplo muestra cómo crear una aplicación en Visual Studio, así como los ejemplos de código que hacen que la aplicación funcione. Siga los pasos que se indican a continuación para crear una aplicación de ejemplo con Aspose.Email.Pop3.

1. Abra Visual Studio.
1. En el **File** menú, seleccionar **New** y luego **Project**.
1. Elija una aplicación de Windows de C# o VB.NET.
1. Importe Aspose.Email.dll a la aplicación haciendo clic con el botón derecho **Reference** en el Explorador de soluciones.
1. Ahora diseñe una aplicación de Windows como se muestra a continuación.
1. Crea una instancia de Pop3Client.
1. Establezca el nombre de host POP3, el inicio de sesión y la contraseña en esta instancia.
1. Llame a las funciones Connect () y Login () de Pop3Client.
1. Crea una instancia de MailMessage y recupera en ella el primer correo electrónico de tu cuenta llamando a la función fetchMessage (). Esto lleva el primer mensaje de tu cuenta de correo electrónico a la instancia de MailMessage.
1. Usa las propiedades From, Subject y HTMLBody de la instancia MailMessage para ver el remitente, el asunto y el cuerpo del mensaje.

Los pasos anteriores se muestran en los ejemplos de código que aparecen a continuación. Usa el siguiente código detrás de cualquier botón o en el evento onLoad de un formulario.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-AsposeEmailPop3.cs" >}}



Para los servidores habilitados para SSL, necesitamos cambiar las siguientes propiedades del objeto Pop3Client:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Imap**
[Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap) implementa el Protocolo de acceso a mensajes de Internet (IMAP) en los marcos de.NET. Aspose.Email.Imap permite a los desarrolladores de.NET agregar capacidades de IMAP a sus aplicaciones.NET rápidamente, sin tener que entender los detalles del protocolo. El componente permite buscar y cargar mensajes, comprobar el estado de los mensajes nuevos, leídos o no leídos, etc.
### **Imap: Características principales**
Aspose.Email.Imap le permite:

- Busca mensajes de correo electrónico.
- Sube mensajes de correo electrónico.
- Enumera los mensajes de correo electrónico en diferentes carpetas.
- Comprueba el estado de los mensajes de correo electrónico.
- Trabaja con MailMessage.
- Trabaja con soporte SSL.
### **Uso de Aspose.Email.Imap**
Aspose.Email.Imap implementa el Protocolo de acceso a mensajes de Internet en marcos de.NET. Con él, los desarrolladores pueden consultar y administrar fácilmente los correos electrónicos del servidor IMAP y crear, eliminar o cambiar el nombre de las carpetas de correo electrónico. Con Aspose.Email.Imap, los desarrolladores pueden aprovechar el protocolo IMAP con API fáciles de usar. Pueden acceder a los correos electrónicos desde cualquier PC, ya que los correos electrónicos permanecen guardados en el servidor. Con Aspose.Email.Imap, los desarrolladores pueden crear aplicaciones web o de escritorio que reciban y manipulen correos electrónicos de servidores IMAP. Aspose implementó el protocolo IMAP de acuerdo con los estándares RFC y de autenticación de Internet. Por lo tanto, Aspose.Email.Imap es una implementación segura y con todas las funciones del protocolo IMAP con un modelo de objetos e interfaces fáciles de entender.
### **Imap: Ejemplo de aplicación**
En este artículo se explica cómo usar [Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap). Creamos una pequeña aplicación que obtiene la cantidad de mensajes de correo electrónico en su cuenta de correo electrónico IMAP. Siga los pasos que se indican a continuación para crear una aplicación de ejemplo con Aspose.Email.Imap.

1. Abra Visual Studio.
1. En el **File** menú, seleccionar **New** y luego **Project**.
1. Elija una aplicación de Windows de C# o VB.NET.
1. Importe el Aspose.Email.dll a esta aplicación haciendo clic con el botón derecho en **Reference** en el Explorador de soluciones.
1. Crea una instancia de IMAPClient pasando el nombre, el nombre de usuario y la contraseña del servidor IMAP.
1. Llame a la función Connect () de la instancia de ImapClient para conectarse al servidor.
1. Llama a la función selectFolder () de la instancia de IMAPClient para seleccionar la carpeta en la que quieres contar el número de mensajes.
1. Ahora llame a la propiedad currentFolder.totalMessageCount de la instancia de IMAPClient para obtener el recuento de mensajes de correo electrónico.
### **Imap: Ejemplos de código**
Los ejemplos de código que aparecen a continuación van detrás del botón o del evento OnLoad de un formulario. Muestran cómo implementar los pasos descritos anteriormente con Aspose.Email.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-AsposeEmailIMAP.cs" >}}



Para los servidores de correo con SSL activado, defina las siguientes propiedades del objeto IMAPClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Exchange**
[Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index) permite a los desarrolladores administrar los correos electrónicos en Microsoft Exchange Server. Con este componente, puede conectarse, enumerar mensajes y descargar correos electrónicos desde el buzón del servidor Exchange sin comprender los detalles del protocolo subyacente. El componente permite enumerar mensajes, enviar correos electrónicos, descargar mensajes y guardarlos en formato eml o msg en su disco local, etc.
### **Exchange: características principales**
Aspose.Email.Exchange le permite:

- Conéctese a los servidores Microsoft Exchange.
- Enumera los mensajes de correo electrónico de los buzones de Exchange.
- Enumera los mensajes de correo electrónico de diferentes carpetas, por ejemplo, las carpetas Bandeja de entrada, Enviados, Eliminados o Borradores.
- Elimine los mensajes de cualquier carpeta de los servidores Exchange.
### **Uso de Aspose.Email.Exchange**
Con Aspose.Email.Exchange, los desarrolladores pueden acceder a los buzones de Exchange Server desde sus aplicaciones.NET. Proporciona una API fácil de usar para administrar los correos electrónicos en los servidores de Exchange. Los desarrolladores pueden crear aplicaciones web, de escritorio o de consola que administren los correos electrónicos en los buzones de Exchange.
## **Ejemplo de aplicación Aspose.Email.Exchange**
En este artículo se muestra cómo usar [Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index). Creamos una aplicación de escritorio sencilla que se conecta a un buzón de Exchange Server, obtiene la lista de mensajes de la carpeta Bandeja de entrada y los muestra en el formulario de Windows.
### **Exchange: ejemplos de pasos de solicitud**
1. Abre Microsoft Visual Studio.
1. Crea un proyecto nuevo. (Seleccione el idioma de su elección: C# o VB.NET)
1. Agregue una referencia a Aspose.Email.dll en su proyecto haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar referencia** del menú.
1. Diseñe un formulario de Windows como el siguiente:

Para ejecutar la aplicación correctamente, necesita las credenciales correctas para acceder a Exchange Server. Aquí obtenemos la información de credenciales (URI, nombre de usuario, contraseña y dominio del servidor Exchange) del formulario de Windows. Este es un ejemplo muy básico, por lo que las propiedades del mensaje (asunto, origen y destino) se muestran simplemente en el cuadro de lista.
### **Exchange: ejemplos de código**
Agregue el siguiente código al controlador de pares de clics del **Listar mensajes** button.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailExchangeSampleApp-AsposeEmailExchange.cs" >}}
### **Intercambio: Salida**
Esta captura de pantalla muestra los mensajes extraídos del servidor Exchange. El método listMessages () devuelve la información básica, como el asunto, el origen y el identificador del mensaje. Para obtener el mensaje completo, llama al método exchangeClient.saveMessage (). (El uso del ExchangeClient.saveMessage () se describe en el artículo [Guardar mensajes del buzón de Exchange Server en formato EML y MSG](/email/net/working-with-exchange-mailbox-and-messages/#saving-messages).)

|![todo:image_alt_text](introduction-and-sample-applications_1.png)|
|: - |
## **Aspose.Email.Mime**
Las extensiones multipropósito de correo de Internet (MIME) son un estándar de Internet que amplía el formato del correo electrónico para admitir texto en conjuntos de caracteres distintos de US-ASCII, archivos adjuntos que no sean de texto, cuerpos de mensajes con varias partes e información de encabezados en conjuntos de caracteres que no sean ASCII. Aspose.Email.Mime implementa el protocolo MIMI en los marcos de.NET. Actúa como un traductor, ya que puede leer un correo electrónico desde un archivo (.eml, etc.) o desde la memoria (cadena). A continuación, analiza el archivo o la cadena de correo electrónico en partes significativas. Si quieres revisar un archivo de correo electrónico sin tener que preocuparte por los detalles del protocolo MIME (por ejemplo, para extraer un archivo adjunto de un correo electrónico), usa Aspose.Email.Mime.
### **Características principales**
Aspose.Email.Mime funciona perfectamente con Aspose.Email.Pop3 y Aspose.Email.Mail.

- [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) recupera los mensajes de correo electrónico de un buzón especificado.
- [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) envía mensajes de correo electrónico a un buzón específico.
- [Aspose.Email.Mime](https://apireference.aspose.com/email/net/aspose.email.mime) es la bisagra de los dos anteriores y analiza los mensajes de correo electrónico.
