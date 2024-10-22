---
title: "Limitaciones y Diferencias en la API"
description: "La biblioteca de análisis de correos electrónicos de C++ tiene algunas diferencias en comparación con su versión equivalente en .NET. Esta página contiene información sobre toda la funcionalidad que no está disponible en la API."
url: /es/cpp/limitations-and-api-differences/
weight: 10
type: docs
---

Aspose.Email para C++ tiene algunas diferencias en comparación con su versión equivalente en .NET de la API. Esta página contiene información sobre toda la funcionalidad que no está disponible en la API.
## **Limitaciones de la API**
Aspose.Email para C++ tiene las siguientes limitaciones que lo hacen diferente de otras APIs de la familia de productos Aspose.Email. Estas son:

- En este momento, la API soporta los siguientes protocolos de comunicación:
  - SMTP
  - POP3
  - IMAP
- La API no soporta Exchange (WebDav así como EWS)
- Sin soporte para formatos de archivo MBox de Thunderbird
- No soporta Encriptación/Desencriptación de Mensajes
- Soporte para la conversión de MapiMessage a MailMessage tampoco está presente
- Recibir notificaciones y Acuses de recibo
- Crear correos electrónicos TNEF a partir de archivos MSG
- Detectar tipo de mensaje tampoco es soportado
- Trabajar con recurrencias que incluyen EndAfterNoccurrences, WeeklyEndAfterNoccurrences, EndAfterNoccurrenceSelectMultipleDaysInweek, MonthlyEndAfterNoccurrences
- Detectar Mensaje como TNEF
- Detectar mensaje incrustado utilizando la bandera Embedded
- Eliminar Recursos vinculados en una ubicación específica
- Renderizar eventos de calendario basados en plantillas de formato
- Eliminar elementos secundarios de las carpetas de archivos PST
- Cambiar propiedades del mensaje en la carpeta de PST utilizando ChangeMessages