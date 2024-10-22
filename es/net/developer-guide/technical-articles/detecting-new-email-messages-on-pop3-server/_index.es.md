---
title: "Detección de Nuevos Mensajes de Correo Electrónico en el Servidor POP3"
url: /es/net/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---

Con cuentas POP3 puedes dejar mensajes en el servidor al descargarlos y leerlos. Dejar correos electrónicos en el servidor significa que están disponibles para otras aplicaciones e individuos, por ejemplo, usuarios que acceden a su correo desde varios dispositivos. O puede que desees descargar solo mensajes que cumplan con ciertos criterios especiales, por ejemplo, mensajes con una línea de asunto particular. Para gestionar el correo electrónico, puedes;

- Leer todos los mensajes del servidor de correo POP3 usando Aspose.Email.
- Descargar los mensajes a tu base de datos local.

Los mensajes no se eliminan, sino que permanecen en el servidor. La primera vez que se ejecuta, este proceso funciona bien. Todos los mensajes requeridos se descargan a la base de datos. Pero la segunda vez que se ejecuta, se descargan los mismos mensajes porque aún están en el servidor de correo. Esto causa registros duplicados. Para resolver este problema, utiliza la propiedad [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3messageinfo/properties/uniqueid) para verificar si un mensaje ya ha sido descargado. El ID único del mensaje debe ser almacenado en la base de datos: es la clave de búsqueda para detectar nuevos mensajes.
## **Detección de Nuevos Mensajes**
Para identificar nuevos correos electrónicos de una lista de correos en un servidor POP3:

1. Conéctate al servidor.
1. Obtén una lista de correos electrónicos.
1. Conéctate a la base de datos.
1. Obtén una lista de correos electrónicos.
1. Compara las listas.
1. Guarda los nuevos correos electrónicos en la base de datos.

El proceso es más rápido cuando:

1. Recuperas todos los IDs únicos de los mensajes en una tabla hash.
1. Buscas en la tabla hash en lugar de en la base de datos para cada mensaje de correo en un bucle foreach(…).

En lugar de consultar la base de datos para cada mensaje, lo que requiere muchas llamadas a la base de datos, este método solo requiere una llamada. El siguiente fragmento de código te muestra cómo detectar nuevos mensajes de correo electrónico en el servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-DetectingNewMessages-DetectingNewMessages.cs" >}}