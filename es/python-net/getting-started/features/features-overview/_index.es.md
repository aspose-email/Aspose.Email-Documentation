---
title: "Resumen de características"
url: /es/python-net/features-overview/
weight: 10
type: docs
---

Apose.Email para Python a través de .NET se divide en varios componentes separados, cada uno con características particulares. Aquí hay una lista de las características de cada uno de los principales paquetes.
## **Aspose.Email.Mail**
### **Características Generales de Email**
- Crear correos electrónicos que contengan texto plano
- Crear correos electrónicos que contengan HTML
- Crear cuerpos de mensajes alternativos para compatibilidad con clientes de correo electrónico que soporten tanto HTML como no-HTML
- Conectarse a cualquier servidor SMTP en un puerto especificado
- Enviar correos electrónicos a través de cualquier servidor SMTP
- Conectarse a un servidor SMTP habilitado para SSL
- Conectarse a un servidor SMTP basado en TLS
### **Características de Adjunto**
- Agregar adjuntos a sus correos electrónicos
- Eliminar adjuntos de sus correos electrónicos
- Crear adjuntos a partir de rutas de archivo
### **Características de Objetos Integrados**
- Incrustar objetos (como imágenes, sonidos, etc.) en sus correos electrónicos.
- Eliminar objetos incrustados de sus correos electrónicos.
- Incrustar objetos a partir de rutas de archivo.
- Incrustar objetos a partir de flujos.
- Incrustar objetos a partir de arreglos de bytes.
### **Características de Importación/Exportación**
- Importar mensajes de correo electrónico en formato Microsoft Outlook Email Message (MSG).
- Importar correos electrónicos en formato Microsoft HTML (MHT)
- Importar correos electrónicos en formato de mensaje compatible con RFC822 (EML)
- Crear correos electrónicos a partir de contenidos HTML
- Exportar correos electrónicos a formato Microsoft HTML (MHT)
- Exportar correos electrónicos a formato de mensaje compatible con RFC822 (EML)
- Exportar correos electrónicos de un archivo PST de Outlook a archivos MSG de Outlook
### **Características de Correo Masivo**
- Soporta el envío de correos electrónicos en lotes.
- Función de múltiples hilos incorporada para enviar correos electrónicos masivos.
- Soporta guardar mensajes de correo electrónico masivo en un pool de mensajes
### **Características de Calendario**
- Agregar eventos iCalender a mensajes de correo electrónico.
- Cancelar eventos iCalendar.
- Enviar solicitudes de reunión por correo electrónico.
- Enviar solicitudes de cita por correo electrónico.
### **Características de Utilidad**
- Personalizar encabezados de correo electrónico.
- Establecer prioridad, fecha y hora del mensaje.
- Soporta todos los conjuntos de caracteres.
- Solicitar acuses de recibo.
### **Características Avanzadas**
- Modelos de programación asíncronos y síncronos.
- Soporta el análisis de correos electrónicos en formatos MSG, MHT y EML.
- Soporta guardar correos electrónicos en formatos MSG, MHT y EML.
- Extraer adjuntos de archivos Microsoft Outlook Email Message (MSG).
- Leer mensajes de archivos PST de Outlook.
- Soporta conexión SMTP de respaldo.
- Especificar el número de intentos para conexiones SMTP.
## **Aspose.Email.Mime**
{{% alert %}}
**¡Pruébalo!**

Analiza archivos de correo electrónico con la gratuita [**Aspose.Email Parser App**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
### **Características Generales de Análisis**
- Extraer encabezados de correo electrónico y cuerpos de mensajes.
- Recuperar nombres y valores de encabezados de correo electrónico.
- Recuperar direcciones From, To, Cc y Reply-To.
- Recuperar y guardar adjuntos.
- Recuperar y guardar objetos incrustados como imágenes y sonidos.
### **Características de Importación/Exportación**
- Importar correos electrónicos en formato Microsoft Outlook Email Message (MSG).
- Importar correos electrónicos en formato Microsoft HTML (MHT).
- Importar correos electrónicos en formato de mensaje compatible con RFC822 (EML).
- Exportar correos electrónicos a formato Microsoft HTML (MHT).
- Exportar correos electrónicos a formato de mensaje compatible con RFC822 (EML).
### **Características de Utilidad**
- Soporta múltiples encabezados.
- Soporta múltiples partes.
- Soporta todos los conjuntos de caracteres.
- Recuperar metadatos como contentType, MimeVersion y XMailer.

{{% alert %}}
**¡Pruébalo!**

Usa [**Aspose.Email Metadata App**](https://products.aspose.app/email/es/metadata) para ver y editar metadatos en línea, propiedades integradas o propiedades personalizadas del mensaje.
{{% /alert %}}
### **Características Avanzadas de Análisis**
- Cargar y analizar correos electrónicos en formatos MSG, MHT y EML.
## **Aspose.Email.Pop3**
### **Características Generales de POP3**
- Recuperar mensajes completos o solo encabezados.
- Soporta comandos básicos de POP3.
- Listar mensajes de correo.
- Recuperar correos electrónicos en formatos MIME y texto plano.
- Recuperar información del buzón de correo.
- Mantener la conexión POP3 activa.
- Características de gestión de correos electrónicos.
- Eliminar correos electrónicos seleccionados en el servidor POP3.
- Eliminar todos los correos electrónicos.
- Cancelar eliminación en el servidor POP3.
- Conectarse a un servidor POP3 habilitado para SSL.
### **Características de Seguridad**
- Soporta el Protocolo de Oficina Post Autenticado (APOP).
- Soporta autenticación de texto claro USER/PASS.
- Soporta autenticación CRAM-MD5 RFC 2195.
- Soporta autenticación DIGEST-MD5 RFC 2831.
- Soporta autenticación de inicio de sesión.
- Soporta autenticación de texto plano TLS RFC 2595.
## **Aspose.Email.Imap**
### **Características Generales**
- Conectarse y comunicarse con servidores IMAP.
- Manipular mensajes de correo y carpetas en el servidor.
- Conectarse a un servidor IMAP habilitado para SSL.
- Recibir notificaciones cuando se recibe un correo electrónico, evitando así la consulta repetitiva al servidor.
### **Características de Gestión de Mensajes**
- Recuperar mensajes de correo electrónico.
- Recuperar encabezados de mensajes de correo electrónico.
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
- Soporta autenticación CRAM-MD5 RFC 2195.
- Soporta autenticación DIGEST-MD5 RFC 2831.
- Soporta autenticación de inicio de sesión.
- Soporta autenticación de texto plano TLS RFC 2595.
## **Aspose.iCalendar**
- Calcular fechas y horas de ocurrencia de manera fácil y confiable, incluso para los patrones de recurrencia más complejos.
- Consumir y producir patrones de recurrencia en formato iCalendar (RFC 2445).
- Crear patrones de recurrencia programáticamente a través de un modelo de objeto intuitivo.
- Usar patrones de recurrencia anuales, mensuales, semanales, diarios, horarios, por minutos y por segundos.
- Representar patrones de recurrencia en sus aplicaciones de Windows, web o móviles.
### **Protocolos Soportados**
- SMTP
- MIME
- POP3
- IMAP
- HTTP
## **Soporte para Archivos PST/OST**
- Soporte para archivos de Almacenamiento Personal y Almacenamiento Offline
- Generar y leer archivos OST, PST
- Soporta archivos PST de todos los tipos
- Todos los tipos de OST soportados para lectura