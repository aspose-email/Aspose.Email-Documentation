---
title: "Detección de nuevos mensajes de correo electrónico en el servidor POP3"
url: /es/net/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---


Con las cuentas POP3 puedes dejar mensajes en el servidor al descargarlos y leerlos. Dejar los correos electrónicos en el servidor significa que están disponibles para otras aplicaciones e individuos, por ejemplo, los usuarios que acceden a su correo electrónico desde varios dispositivos. O tal vez quieras descargar solo los mensajes que cumplan algunos criterios especiales, por ejemplo, los mensajes con un asunto determinado. Para administrar el correo electrónico, puedes:

- Lea todos los mensajes del servidor de correo POP3 mediante Aspose.Email.
- Descargue los mensajes a su base de datos local.

Los mensajes no se eliminan, sino que permanecen en el servidor. La primera vez que se ejecuta, este proceso funciona bien. Todos los mensajes necesarios se descargan a la base de datos. Pero la segunda vez que se ejecuta, se descargan los mismos mensajes porque siguen en el servidor de correo electrónico. Esto provoca registros duplicados. Para resolver este problema, utilice el [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3messageinfo/properties/uniqueid) propiedad para comprobar si un mensaje ya se ha descargado. El identificador único del mensaje debe almacenarse en la base de datos: es la clave de búsqueda para detectar nuevos mensajes.
## **Detección de mensajes nuevos**
Para identificar nuevos correos electrónicos de una lista de correos electrónicos en un servidor POP3:

1. Conéctese al servidor.
1. Obtenga una lista de correos electrónicos.
1. Conéctese a la base de datos.
1. Obtenga una lista de correos electrónicos.
1. Compara las listas.
1. Guarde los correos electrónicos nuevos en la base de datos.

El proceso es más rápido cuando:

1. Obtenga todos los ID únicos de los mensajes en una tabla hash.
1. Busca en la tabla hash en lugar de en la base de datos para cada mensaje de correo electrónico en un bucle foreach (...).

En lugar de consultar la base de datos para cada mensaje, lo que requiere muchas llamadas a la base de datos, este método solo requiere una llamada. El siguiente fragmento de código muestra cómo detectar nuevos mensajes de correo electrónico en el servidor POP3.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-DetectingNewMessages-DetectingNewMessages.cs" >}}
