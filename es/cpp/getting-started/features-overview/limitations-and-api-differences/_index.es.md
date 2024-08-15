---
title: "Limitaciones y diferencias de API"
description: "La biblioteca de analizadores de correo electrónico de C++ tiene algunas diferencias en comparación con su versión de.NET equivalente. Esta página contiene información sobre todas estas funciones que no están disponibles en la API."
url: /es/cpp/limitations-and-api-differences/
weight: 10
type: docs
---

Aspose.Email para C++ presenta algunas diferencias en comparación con la versión .NET equivalente de la API. Esta página contiene información sobre todas estas funciones que no están disponibles en la API.
## **Limitaciones de la API**
Aspose.Email para C++ tiene las siguientes limitaciones que la diferencian de otras API de la familia de productos Aspose.Email. Estas son:

- Por el momento, la API admite los siguientes protocolos de comunicación:
  - SMTP
  - POP3
  - IMAP
- La API no es compatible con Exchange (WebDAV y EWS)
- No hay soporte para los formatos de archivo MBox de Thunderbird
- No admite el cifrado/descifrado de mensajes
- El soporte para la conversión de mapiMessage a MailMessage tampoco está presente.
- Recibir notificaciones y leer recibos
- Creación de correos electrónicos TNEF a partir de archivos MSG
- Tampoco se admite la detección del tipo de mensaje
- Trabajando con recurrencias, incluidas EndAfterOccurrences, WeeklyEndAfterOccurrences, EndAfterNoccurrenceSeleccione varios días de la semana y MonthlyEndAfterOccurrences
- Detección de mensaje como TNEF
- Detección de mensajes incrustados mediante el indicador incorporado
- Eliminar los recursos enlazados en una ubicación específica
- Representación de eventos de calendario en función de plantillas de formato
- Eliminar elementos infantiles de las carpetas del archivo PST
- Cambiar las propiedades de los mensajes en la carpeta de PST mediante ChangeMessages
