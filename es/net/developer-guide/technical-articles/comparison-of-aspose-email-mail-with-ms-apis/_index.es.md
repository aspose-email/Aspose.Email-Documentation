---
title: "Comparación de Aspose.Email.Mail con las API de MS"
url: /es/net/comparison-of-aspose-email-mail-with-ms-apis/
weight: 20
type: docs
---

## **Comparación de Aspose Email Mail con las API de MS**
System.Web.Mail es simplemente un contenedor de dos bibliotecas COM: cdonts.NewMail (que se encuentra en cdonts.dll) y cdo.Message (que se encuentra en cdosys.dll). También necesitará que estén instaladas en su servidor. De forma predeterminada, cdonts.dll y cdosys.dll se instalan con WindowsNT/2000/XP/2003.
### **Especificaciones de SMTPmail**
Si rastreas la clase System.Web.Mail.SmtpMail, encontrarás algunos comportamientos extraños:

- Solo es compatible con los sistemas operativos Win32NT, por ejemplo, Windows 2000, Windows 2003, Windows XP.
- Cuando la clase SMTPMail envía un mensaje de correo, comprueba la versión del sistema operativo. Si la versión es <= 4, se usa el objeto cdonts.newMail; para todos los sistemas operativos superiores a 4, se usa el objeto cdo.Message.

Estas peculiaridades hacen que la solución de problemas sea mucho más difícil, especialmente al mover código a diferentes sistemas operativos. La aplicación puede obtener resultados inesperados en diferentes sistemas operativos. Aspose.Email.Mail es un componente de.NET escrito en código totalmente administrado en C# puro. No depende de ninguna biblioteca COM, incluidas cdonts.NewMail o CDO.Message. Con Aspose.Email.Mail, evita invocar ningún código no administrado en sus aplicaciones, lo que aumenta la confiabilidad y se libera de la aburrida depuración de COM. Aspose.Email.Mail tiene muchas funciones y proporciona muchos más servicios que los que ofrece la arquitectura System.Web.Mail. System.Net.Mail es una nueva implementación de cliente de protocolo SMTP en .NET 2.0. También es una implementación de código administrado puro en C#.
### **Matriz de comparación**

|**Features** |**Aspose.Email.Mail** |**System.Web.Mail** |**System.Net.Mail** |
|: - |: - |: - |: - |
|Características de compatibilidad | | | |
|Soporta .NET 2.0 |X |X |X |
|Características comunes | | | |
|Dependencia de CDO/CDONTS | |X | |
|Código gestionado puro |X | |X |
|Autenticación |X |X |
|Dirección del remitente |X |X |
|Dirección del destinatario |X |X |
|Cuerpo HTML |X |X |X |
|Cuerpo del texto |X |X |X |
|Bcc/Cc |X |X |
|Enviar archivo adjunto |X |X |
|Imagen vinculada |X | |X |
|Codificación corporal (Unicode/ASCII) |X |X |
|Codificación del sujeto (Unicode/ASCII) |X | |X |
|Modelo de programación sincrónica |X | |X |
|Modelo de programación asincrónica |X | |X |
|Características únicas | | | |
|Encabezado de correo personalizado |X | | |
|Encabezado de importancia |X | | |
|Encabezado de sensibilidad |X | | |
|Encabezado de X-Mailer |X | | |
|Responder a |X | | |
|Fecha de envío |X | | |
|Combinación de correspondencia basada en plantillas |X | | |
|Combinación de correspondencia desde un conjunto de datos |X | | |
|Combinar correspondencia desde DataTable |X | | |
|Combinar correspondencia desde DataReader |X | | |
|Envío masivo con subprocesos múltiples |X | | |
|Enviar calendario |X | | |
|Enviar solicitud de reunión |X | | |
|Cargar desde el formato Microsoft Msg |X | | |
|Cargar desde el formato Microsoft Mht |X | | |
|Guardar en formato Microsoft Mht |X | | |
|Guardar en formato Eml |X | | |
|Cargar desde el formato Eml |X | | |
|Cargar desde un archivo compatible con la RFC 822 |X | | |
|Características de interoperación | | | |
| Funciona con Aspose.Email.Pop3 |X | | |
| Funciona con Aspose.Email.Imap | X | | |
| Funciona con Aspose.Email.Mime | X | | |

