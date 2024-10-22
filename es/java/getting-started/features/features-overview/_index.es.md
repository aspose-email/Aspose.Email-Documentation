---
title: "Resumen de Características"
url: /es/java/features-overview/
weight: 10
type: docs
---

Apose.Email para Java está dividido en varios componentes separados, cada uno con características particulares. Aquí hay una lista de las características de cada uno de los paquetes principales.
## **Aspose.Email.Mail**
### **Características Generales de Email**
- Crear correos electrónicos que contengan texto plano
- Crear correos electrónicos que contengan HTML
- Crear cuerpos de mensaje alternativos para la compatibilidad con clientes de correo electrónico que soportan HTML y no HTML
- Conectar con cualquier servidor SMTP en un puerto especificado
- Enviar correos electrónicos a través de cualquier servidor SMTP
- Conectar a un servidor SMTP habilitado para SSL
- Conectar a un servidor SMTP basado en TLS
### **Características de Adjuntos**
- Agregar adjuntos a correos electrónicos
- Eliminar adjuntos de correos electrónicos
- Crear adjuntos a partir de rutas de archivo
- Crear adjuntos a partir de flujos
- Crear adjuntos a partir de arreglos de bytes
### **Características de Objetos Embebidos**
- Incrustar objetos (como imágenes, sonidos, etc.) en tus correos electrónicos
- Eliminar objetos embebidos de tus correos electrónicos
- Incrustar objetos a partir de rutas de archivo
- Incrustar objetos a partir de flujos
- Incrustar objetos a partir de arreglos de bytes
### **Características de Importación/Exportación**
- Importar correos electrónicos en formato Microsoft Outlook Email Message (MSG).
- Importar correos electrónicos en formato HTML de Microsoft (MHT)
- Importar correos electrónicos en formato de mensaje conforme a RFC822 (EML)
- Crear correos electrónicos a partir de contenidos HTML
- Exportar correos electrónicos a formato HTML de Microsoft (MHT)
- Exportar correos electrónicos a formato de mensaje conforme a RFC822 (EML)
- Exportar correos electrónicos desde un archivo PST de Outlook a archivos MSG de Outlook
### **Características de Correo Masivo**
- Soporta el envío de correos electrónicos en lotes
- Característica de multihilo incorporada para el envío de correos electrónicos masivos
- Soporta guardar mensajes de correo masivo en un grupo de mensajes
### **Características de Combinar Correspondencia**
- Combinar correspondencia basada en plantillas utilizando diferentes fuentes de datos
- Soporta DataTable como fuente de datos
- Soporta DataRowCollection como fuente de datos
- Soporta DataReader como fuente de datos
- Crear plantilla de correo electrónico a partir de un archivo
- Crear plantilla de correo electrónico a partir de una instancia de MailMessage
- Realizar combinación de correspondencia fila por fila para generar mensajes de correo electrónico
### **Características de Calendario**
- Agregar eventos de iCalendar a los mensajes de correo electrónico.
- Cancelar eventos de iCalendar.
- Enviar solicitudes de reunión por correo electrónico.
- Enviar solicitudes de cita por correo electrónico.
### **Características de Manejo de Eventos**
- Soporta una variedad de eventos útiles para proporcionar más control.
- Realizar acciones cuando se envían todos los correos electrónicos masivos.
- Realizar acciones cuando un mensaje está a punto de ser enviado.
- Ser notificado a través de un evento cuando un correo electrónico se ha enviado completamente.
### **Características de Utilidad**
- Personalizar los encabezados de correo electrónico.
- Establecer prioridad, fecha y hora del mensaje.
- Soporta todos los conjuntos de caracteres.
- Solicitar confirmaciones de lectura.
### **Características Avanzadas**
- Modelos de programación asincrónicos y sincrónicos.
- Soporta el análisis de correos electrónicos en formatos MSG, MHT y EML.
- Soporta guardar correos electrónicos en formatos MSG, MHT y EML.
- Extraer adjuntos de archivos de Microsoft Outlook Email Message (MSG).
- Leer mensajes de archivos PST de Outlook.
- Soporta conexión SMTP de respaldo.
- Especificar el número de intentos para las conexiones SMTP.
## **Aspose.Email.Mime**
{{% alert %}}
**¡Pruébalo!**

Analiza archivos de correo electrónico con la gratuita [**Aplicación Aspose.Email Parser**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
### **Características Generales de Análisis**
- Extraer encabezados de correo electrónico y cuerpos de mensajes.
- Recuperar nombres y valores de los encabezados de correo electrónico.
- Recuperar direcciones From, To, Cc y Reply-To.
- Recuperar y guardar adjuntos.
- Recuperar y guardar objetos embebidos como imágenes y sonidos.
### **Características de Importación/Exportación**
- Importar correos electrónicos en formato Microsoft Outlook Email Message (MSG).
- Importar correos electrónicos en formato HTML de Microsoft (MHT).
- Importar correos electrónicos en formato de mensaje conforme a RFC822 (EML).
- Exportar correos electrónicos a formato HTML de Microsoft (MHT).
- Exportar correos electrónicos a formato de mensaje conforme a RFC822 (EML).
### **Características de Utilidad**
- Soporta múltiples encabezados.
- Soporta múltiples partes.
- Soporta todos los conjuntos de caracteres.
- Recuperar metadatos como contentType, MimeVersion y XMailer.

{{% alert %}}
**¡Pruébalo!**

Usa [**Aplicación Aspose.Email Metadata**](https://products.aspose.app/email/es/metadata) para ver y editar metadatos en línea, propiedades incorporadas o propiedades personalizadas del mensaje.
{{% /alert %}}
### **Características Avanzadas de Análisis**
- Cargar y analizar correos electrónicos en formatos MSG, MHT y EML.
## **Aspose.Email.Pop3**
### **Características Generales de POP3**
- Recuperar mensajes completos o solo encabezados.
- Soporta comandos básicos de POP3.
- Listar mensajes de correo.
- Recuperar correos electrónicos en formatos MIME y texto plano.
- Recuperar información del buzón.
- Mantener viva la conexión POP3.
- Características de gestión de correos electrónicos.
- Eliminar correos electrónicos seleccionados en el servidor POP3.
- Eliminar todos los correos electrónicos.
- Cancelar eliminación en el servidor POP3.
- Conectar a un servidor POP3 habilitado para SSL.
### **Características de Seguridad**
- Soporta el Protocolo de Oficina de Correos Autenticado (APOP).
- Soporta autenticación de texto claro USER/PASS.
- Soporta autenticación CRAM-MD5 conforme a RFC 2195.
- Soporta autenticación DIGEST-MD5 conforme a RFC 2831.
- Soporta autenticación de inicio de sesión.
- Soporta autenticación TLS de texto claro conforme a RFC 2595.
## **Aspose.Email.Exchange**
### **Características Generales de Exchange**
- Conectar a Microsoft Exchange Server 2003, 2007, 2010 y 2013.
- Recuperar correos electrónicos del servidor de Exchange.
- Listar mensajes de correo.
- Recuperar información del buzón.
- Características de gestión de correos electrónicos.
- Eliminar correos electrónicos seleccionados en el servidor de Exchange.
## **Características de Utilidad**
- Establecer tiempos de espera de conexión y lectura.
- Establecer tamaño de búfer de envío y recepción.
- Obtener identificadores únicos de correos electrónicos en un servidor.
- Recuperar conteo de mensajes.
- Recuperar tamaño del mensaje.
## **Aspose.Email.Imap**
### **Características Generales**
- Conectar y comunicarse con servidores IMAP.
- Manipular mensajes de correo y carpetas en el servidor.
- Conectar a un servidor IMAP habilitado para SSL.
- Ser notificado cuando un correo electrónico es recibido, evitando así solicitar al servidor repetidamente.
### **Características de Gestión de Mensajes**
- Obtener mensajes de correo electrónico.
- Obtener encabezados de los mensajes de correo electrónico.
- Guardar mensajes de correo electrónico en el sistema de archivos local.
- Eliminar mensajes de correo electrónico.
- Listar mensajes de correo electrónico en la carpeta especificada.
- Establecer marcas (leído, eliminar, etc.) para mensajes de correo electrónico especificados.
### **Características de Gestión de Carpetas**
- Crear carpetas de correo electrónico.
- Eliminar carpetas de correo electrónico.
- Renombrar carpetas de correo electrónico.
### **Características de Seguridad**
- Soporta autenticación de texto claro USER/PASS.
- Soporta autenticación CRAM-MD5 conforme a RFC 2195.
- Soporta autenticación DIGEST-MD5 conforme a RFC 2831.
- Soporta autenticación de inicio de sesión.
- Soporta autenticación TLS de texto claro conforme a RFC 2595.
## **Aspose.Email.Verify**
### **Características de Validación**
- Validar direcciones de correo electrónico.
- Soporta validación de sintaxis de correo electrónico.
- Soporta validación de dominio de correo electrónico.
- Soporta validación de servidor de correo.
- Soporta validación de registros MX.
- Validación asincrónica.
- Resultados de validación flexibles.
### **Características de Utilidad**
- Especificar servidores DNS. * Establecer tiempo de espera de solicitud.
## **Aspose.iCalendar**
- Calcular fácilmente y de manera confiable fechas y horas de ocurrencia incluso para los patrones de recurrencia más complejos.
- Consumir y producir patrones de recurrencia en el formato iCalendar (RFC 2445).
- Crear patrones de recurrencia programáticamente a través de un modelo de objeto intuitivo.
- Utilizar patrones de recurrencia anuales, mensuales, semanales, diarios, por hora, por minuto y por segundo.
- Representar patrones de recurrencia en tus aplicaciones de Windows, web o móviles.
## **Soporte para Archivos PST/OST**
- Soporte para archivos de Almacenamiento Personal y Offline
- Generar y leer archivos OST, PST
- Soporta archivos PST de todos los tipos
- Todos los tipos de OST soportados para lectura
## **Protocolos Soportados**
- SMTP
- MIME
- POP3
- IMAP
- HTTP