---
title: "Detección de nuevos mensajes de correo electrónico en el servidor POP3"
url: /es/java/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---


Con las cuentas POP3 puedes dejar mensajes en el servidor al descargarlos y leerlos. Dejar los correos electrónicos en el servidor significa que están disponibles para otras aplicaciones e individuos, por ejemplo, los usuarios que acceden a su correo electrónico desde varios dispositivos. O tal vez quieras descargar solo los mensajes que cumplan algunos criterios especiales, por ejemplo, los mensajes con un asunto determinado. Para administrar el correo electrónico, puedes:

- Lea todos los mensajes del servidor de correo POP3 mediante Aspose.Email.
- Descargue los mensajes a su base de datos local.

Los mensajes no se eliminan, sino que permanecen en el servidor. La primera vez que se ejecuta, este proceso funciona bien. Todos los mensajes necesarios se descargan a la base de datos. Pero la segunda vez que se ejecuta, se descargan los mismos mensajes porque siguen en el servidor de correo electrónico. Esto provoca registros duplicados. Para resolver este problema, utilice el [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/email/java/com.aspose.email/Pop3MessageInfo#getUniqueId\(\)) propiedad para comprobar si un mensaje ya se ha descargado. El identificador único del mensaje debe almacenarse en la base de datos: es la clave de búsqueda para detectar nuevos mensajes.
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
1. Busque en la tabla hash en lugar de en la base de datos para cada mensaje de correo electrónico en un bucle for (...).

En lugar de consultar la base de datos para cada mensaje, lo que requiere muchas llamadas a la base de datos, este método solo requiere una llamada. El siguiente fragmento de código muestra cómo detectar nuevos mensajes de correo electrónico en el servidor POP3.



~~~Java
public static void run() {
    try {
        // Connect to the POP3 mail server and check messages.
        Pop3Client pop3Client = new Pop3Client("pop.domain.com", 993, "username", "password");

        // List all the messages
        Pop3MessageInfoCollection msgList = pop3Client.listMessages();
        for (Pop3MessageInfo msgInfo : msgList) {
            // Get the POP3 message's unique ID
            String strUniqueID = msgInfo.getUniqueId();

            // Search your local database or data store on the unique ID. If a match is found, that means it's already downloaded. Otherwise download and save it.
            if (searchPop3MsgInLocalDB(strUniqueID) == true) {
                // The message is already in the database. Nothing to do with this message. Go to next message.
            } else {
                // Save the message
                savePop3MsgInLocalDB(msgInfo);
            }
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }

}

private static void savePop3MsgInLocalDB(Pop3MessageInfo msgInfo) {
    // Open the database connection according to your database. Use public properties (for example msgInfo.Subject) and store in database,
    // for example, " INSERT INTO POP3Mails (UniqueID, Subject) VALUES ('" + msgInfo.UniqueID + "' , '" + msgInfo.Subject + "') and Run the query to store in database.
}

private static boolean searchPop3MsgInLocalDB(String strUniqueID) {
    // Open the database connection according to your database. Use strUniqueID in the search query to find existing records,
    // for example, " SELECT COUNT(*) FROM POP3Mails WHERE UniqueID = '" + strUniqueID + "' Run the query, return true if count == 1. Return false if count == 0.
    return false;
}
~~~