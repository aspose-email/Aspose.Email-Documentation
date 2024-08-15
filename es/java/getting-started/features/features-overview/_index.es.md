---
title: "Descripción general de las funciones"
url: /es/java/features-overview/
weight: 10
type: docs
---

Apose.Email para Java se divide en varios componentes independientes, cada uno con características particulares. Esta es una lista de las funciones de cada uno de los paquetes principales.
## **Aspose.Email.Mail**
### **Características generales del correo electrónico**
- Crea correos electrónicos que contengan texto sin formato
- Crear correos electrónicos que contengan HTML
- Cree cuerpos de mensajes alternativos para que sean compatibles con clientes de correo electrónico compatibles con HTML y no HTML
- Conéctese con cualquier servidor SMTP en un puerto específico
- Envía correos electrónicos a través de cualquier servidor SMTP
- Conéctese a un servidor SMTP habilitado para SSL
- Conéctese a un servidor SMTP basado en TLS
### **Características de los archivos adjuntos**
- Agregar archivos adjuntos a correos electrónicos
- Eliminar los archivos adjuntos de los correos electrónicos
- Crear archivos adjuntos a partir de rutas de archivos
- Crear archivos adjuntos a partir de transmisiones
- Crear archivos adjuntos a partir de matrices de bytes
### **Características de objetos incrustados**
- Inserta objetos (como imágenes, sonidos, etc.) en tus correos electrónicos
- Elimine los objetos incrustados de sus correos electrónicos
- Incrustar objetos desde rutas de archivos
- Incrustar objetos de transmisiones
- Incrustar objetos de matrices de bytes
### **Funciones de importación/exportación**
- Importe correos electrónicos con formato de mensaje de correo electrónico (MSG) de Microsoft Outlook.
- Importar correos electrónicos HTML (MHT) de Microsoft
- Importar correos electrónicos con formato de mensaje (EML) compatible con RFC822
- Crear correos electrónicos a partir de contenido HTML
- Exportación de correos electrónicos al formato HTML de Microsoft (MHT)
- Exportación de correos electrónicos a un formato de mensaje (EML) compatible con RFC822
- Exportación de correos electrónicos desde un archivo PST de Outlook a archivos MSG de Outlook
### **Funciones de correo masivo**
- Soporta el envío de correos electrónicos en lotes
- Función integrada de subprocesos múltiples para enviar correos electrónicos masivos
- Permite guardar mensajes de correo electrónico masivos en un grupo de mensajes
### **Funciones de combinación de correspondencia**
- Combinación de correspondencia basada en plantillas con diferentes fuentes de datos
- Soporta DataTable como fuente de datos
- Soporta DataRowCollection como fuente de datos
- Soporta DataReader como fuente de datos
- Crear plantilla de correo electrónico a partir de un archivo
- Crear una plantilla de correo electrónico a partir de una instancia de MailMessage
- Realice una combinación de correspondencia por filas para generar mensajes de correo electrónico
### **Características del calendario**
- Agregue eventos de iCalendar a los mensajes de correo electrónico.
- Cancela los eventos de iCalendar.
- Envíe las convocatorias de reunión por correo electrónico.
- Envíe las solicitudes de citas por correo electrónico.
### **Funciones de gestión de eventos**
- Admite una variedad de eventos útiles para proporcionar más control.
- Realice acciones cuando se envíen todos los correos electrónicos masivos.
- Realice acciones cuando esté a punto de enviarse un mensaje.
- Reciba una notificación a través de un evento cuando un correo electrónico se haya enviado por completo.
### **Características de utilidad**
- Personaliza los encabezados de correo electrónico.
- Establece la prioridad, la fecha y la hora de los mensajes.
- Soporta todos los conjuntos de caracteres.
- Solicita recibos de lectura.
### **Funciones avanzadas**
- Modelos de programación asincrónica y sincrónica.
- Soporta el análisis de correos electrónicos en formatos MSG, MHT y EML.
- Permite guardar correos electrónicos en formatos MSG, MHT y EML.
- Extraiga los archivos adjuntos de los archivos de mensajes de correo electrónico (MSG) de Microsoft Outlook.
- Lea los mensajes de los archivos PST de Outlook.
- Soporta conexión SMTP de respaldo.
- Especifique el número de intentos de conexiones SMTP.
## **Aspose.Email.Mime**
{{% alert %}}
**¡Pruébalo!**

Analice archivos de correo electrónico con la versión gratuita [**Aplicación de análisis Aspose.Email**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
### **Funciones generales de análisis**
- Extraiga los encabezados y cuerpos de los mensajes de correo electrónico.
- Recupera nombres y valores de los encabezados de los correos electrónicos.
- Recupere las direcciones de origen, destino, cc y respuesta.
- Recupera y guarda los archivos adjuntos.
- Recupera y guarda objetos incrustados, como imágenes y sonidos.
### **Funciones de importación/exportación**
- Importe correos electrónicos con formato de mensaje de correo electrónico (MSG) de Microsoft Outlook.
- Importe correos electrónicos en formato HTML (MHT) de Microsoft.
- Importe correos electrónicos con formato de mensaje (EML) compatible con RFC822.
- Exporte correos electrónicos al formato HTML de Microsoft (MHT).
- Exporte correos electrónicos a un formato de mensaje (EML) compatible con RFC822.
### **Características de utilidad**
- Soporta múltiples encabezados.
- Soporta múltiples piezas.
- Soporta todos los conjuntos de caracteres.
- Recupera metadatos como ContentType, MimeVersion y XMailer.

{{% alert %}}
**¡Pruébalo!**

Use [**Aplicación de metadatos Aspose.Email**](https://products.aspose.app/email/es/metadata) para ver y editar los metadatos en línea, las propiedades integradas o las propiedades personalizadas del mensaje.
{{% /alert %}}
### **Funciones de análisis avanzado**
- Carga y analiza correos electrónicos en formatos MSG, MHT y EML.
## **Aspose.Email.Pop3**
### **Características generales de POP3**
- Recupera solo los mensajes o encabezados completos.
- Soporta comandos POP3 básicos.
- Enumera los mensajes de correo.
- Recupera correos electrónicos en formato MIME y texto sin formato.
- Recupere la información del buzón.
- Mantenga activa la conexión POP3.
- Funciones de administración de correo electrónico.
- Elimine los correos electrónicos seleccionados en el servidor POP3.
- Elimina todos los correos electrónicos.
- Cancela la eliminación en el servidor POP3.
- Conéctese a un servidor POP3 con SSL habilitado.
### **Características de seguridad**
- Soporta el protocolo de oficina de correos autenticado (APOP).
- Soporta la autenticación USER/PASS de texto sin cifrar.
- Soporta la autenticación RFC 2195 CRAM-MD5.
- Soporta la autenticación DIGEST-MD5 según RFC 2831.
- Soporta la autenticación de inicio de sesión.
- Admite la autenticación de texto plano TLS según RFC 2595.
## **Aspose.Email.Exchange**
### **Características generales de Exchange**
- Conéctese a Microsoft Exchange Server 2003, 2007, 2010 y 2013.
- Recupere correos electrónicos de Exchange Server.
- Enumera los mensajes de correo.
- Recupere la información del buzón.
- Funciones de administración de correo electrónico.
- Elimine los correos electrónicos seleccionados en Exchange Server.
## **Características de utilidad**
- Establezca los tiempos de espera de conexión y lectura.
- Establezca el tamaño del búfer de envío y recepción.
- Obtenga identificadores únicos de los correos electrónicos de un servidor.
- Recuento de mensajes de recuperación.
- Recupera el tamaño del mensaje.
## **Aspose.Email.Imap**
### **Características generales**
- Conéctese y comuníquese con servidores IMAP.
- Manipule los mensajes de correo electrónico y las carpetas del servidor.
- Conéctese a un servidor IMAP con SSL habilitado.
- Reciba una notificación cuando se reciba un correo electrónico, evitando así sondear el servidor repetidamente
### **Funciones de administración de mensajes**
- Busca mensajes de correo electrónico.
- Obtiene los encabezados de los mensajes de correo electrónico.
- Guarde los mensajes de correo electrónico en el sistema de archivos local.
- Eliminar mensajes de correo electrónico.
- Muestra los mensajes de correo electrónico de la carpeta especificada.
- Establezca marcas (leer, eliminar, etc.) para los mensajes de correo electrónico específicos.
### **Funciones de administración de carpetas**
- Crea carpetas de correo electrónico.
- Eliminar carpetas de correo electrónico.
- Cambie el nombre de las carpetas de correo electrónico.
### **Características de seguridad**
- Soporta la autenticación USER/PASS de texto sin cifrar.
- Soporta la autenticación RFC 2195 CRAM-MD5.
- Soporta la autenticación DIGEST-MD5 según RFC 2831.
- Soporta la autenticación de inicio de sesión.
- Admite la autenticación de texto plano TLS según RFC 2595.
## **Aspose.Email.Verify**
### **Funciones de validación**
- Valida las direcciones de correo electrónico.
- Soporta la validación de la sintaxis del correo electrónico.
- Soporta la validación de dominios de correo electrónico.
- Soporta la validación del servidor de correo.
- Soporta la validación de registros MX.
- Validación asincrónica.
- Resultados de validación flexibles.
### **Características de utilidad**
- Especifique los servidores DNS.* Establezca el tiempo de espera de la solicitud.
## **Aspose.iCalendar**
- Calcule de manera fácil y confiable las fechas y horas de ocurrencia incluso para los patrones de recurrencia más complejos.
- Consume y produce patrones de recurrencia en formato iCalendar (RFC 2445).
- Cree patrones de recurrencia mediante programación mediante un modelo de objetos intuitivo.
- Usa patrones de recurrencia anuales, mensuales, semanales, diarios, por hora, por minuto y por segundo.
- Represente los patrones de recurrencia en sus ventanas, la web o una aplicación móvil.
## **Soporte de archivos PST/OST**
- Soporte para archivos de almacenamiento personal y sin conexión
- Generar y leer archivos OST, PST
- Soporta archivos PST de todos los tipos
- Todos los tipos de OST compatibles con la lectura
## **Protocolos compatibles**
- SMTP
- MIME
- POP3
- IMAP
- HTTP
