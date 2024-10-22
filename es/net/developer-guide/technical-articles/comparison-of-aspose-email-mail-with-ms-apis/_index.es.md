---
title: "Comparación de Aspose.Email.Mail con las APIs de MS"
url: /es/net/comparison-of-aspose-email-mail-with-ms-apis/
weight: 20
type: docs
---

## **Comparación de Aspose Email Mail con las APIs de MS**
System.Web.Mail es simplemente un envoltorio alrededor de dos bibliotecas COM: CDONTS.NewMail (encontrada en el cdonts.dll) y CDO.Message (encontrada en el cdosys.dll). También necesitarás tenerlas instaladas en tu servidor. Por defecto, cdonts.dll y cdosys.dll se instalan con WindowsNT/2000/XP/2003.
### **Especificaciones de SmtpMail**
Si rastreas en la clase System.Web.Mail.SmtpMail, encontrarás algunos comportamientos extraños:

- Solo soporta sistemas operativos Win32NT, por ejemplo, Windows 2000, Windows 2003, Windows XP.
- Cuando la clase SmtpMail envía un mensaje de correo, verifica la versión del SO. Si la versión es <= 4, se utiliza el objeto CDONTS.Newmail; para todos los sistemas operativos mayores que 4, se utiliza el objeto CDO.Message.

Estas peculiaridades hacen que la solución de problemas sea mucho más difícil, especialmente al mover código a diferentes sistemas operativos. La aplicación puede obtener resultados inesperados en diferentes SOs. Aspose.Email.Mail es un componente .NET escrito en código completamente administrado en puro C#. No depende en absoluto de ninguna biblioteca COM, incluyendo CDONTS.NewMail o CDO.Message. Con Aspose.Email.Mail evitas invocar cualquier código no administrado en tus aplicaciones, aumentando la confiabilidad y liberándote de la tediosa depuración de COM. Aspose.Email.Mail es rico en características y proporciona muchos más servicios que los proporcionados por la arquitectura System.Web.Mail. System.Net.Mail es una nueva implementación de cliente SMTP en .NET 2.0. También es una implementación de código completamente administrado en C#.
### **Matriz de Comparación**

|**Características** |**Aspose.Email.Mail** |**System.Web.Mail** |**System.Net.Mail** |
| :- | :- | :- | :- |
|Características de Compatibilidad | | | |
|Soporta .NET 2.0 |X |X |X |
|Características Comunes | | | |
|Dependencia de CDO/CDONTS | |X | |
|Código Completamente Administrado |X | |X |
|Autenticación |X |X |X |
|Dirección del Remitente |X |X |X |
|Dirección de los Destinatarios |X |X |X |
|Cuerpo en HTML |X |X |X |
|Cuerpo en Texto |X |X |X |
|Bcc/Cc |X |X |X |
|Enviar Adjunto |X |X |X |
|Imagen Vinculada |X | |X |
|Codificación del Cuerpo (Unicode/ASCII) |X |X |X |
|Codificación del Asunto (Unicode/ASCII) |X | |X |
|Modelo de programación sincrónica |X | |X |
|Modelo de programación asincrónica |X | |X |
|Características Únicas | | | |
|Cabecera de Correo Personalizada |X | | |
|Cabecera de Importancia |X | | |
|Cabecera de Sensibilidad |X | | |
|Cabecera X-Mailer |X | | |
|Responder a |X | | |
|Fecha de Envío |X | | |
|Combinar Correo basado en Plantilla |X | | |
|Combinar Correo desde DataSet |X | | |
|Combinar Correo desde DataTable |X | | |
|Combinar Correo desde DataReader |X | | |
|Envío Masivo con Multi-threading |X | | |
|Enviar Calendario |X | | |
|Enviar solicitud de reunión |X | | |
|Cargar desde el formato Msg de Microsoft |X | | |
|Cargar desde el formato Mht de Microsoft |X | | |
|Guardar en formato Mht de Microsoft |X | | |
|Guardar en formato Eml |X | | |
|Cargar desde formato Eml |X | | |
|Cargar desde archivo compatible con RFC 822 |X | | |
|Características de Interoperabilidad | | | |
|Funciona con Aspose.Email.Pop3 |X | | |
|Funciona con Aspose.Email.Imap |X | | |
|Funciona con Aspose.Email.Mime |X | | |