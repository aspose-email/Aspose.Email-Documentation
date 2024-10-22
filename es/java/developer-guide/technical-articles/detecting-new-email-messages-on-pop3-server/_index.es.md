---
title: "Detectando Nuevos Mensajes de Correo Electrónico en el Servidor POP3"
url: /es/java/detectando-nuevos-mensajes-de-correo-electronico-en-el-servidor-pop3/
weight: 100
type: docs
---

Con cuentas POP3 puedes dejar mensajes en el servidor al descargarlos y leerlos. Dejar correos electrónicos en el servidor significa que están disponibles para otras aplicaciones e individuos, por ejemplo, usuarios que acceden a su correo electrónico desde varios dispositivos. O podrías querer descargar solo mensajes que cumplan con ciertos criterios especiales, por ejemplo, mensajes con una línea de asunto particular. Para gestionar el correo electrónico, puedes;

- Leer todos los mensajes del servidor de correo POP3 utilizando Aspose.Email.
- Descargar los mensajes en tu base de datos local.

Los mensajes no se eliminan, sino que permanecen en el servidor. La primera vez que se ejecuta, este proceso funciona bien. Todos los mensajes requeridos se descargan en la base de datos. Pero la segunda vez que se ejecuta, se descargan los mismos mensajes porque todavía están en el servidor de correo. Esto provoca registros duplicados. Para resolver este problema, usa la propiedad [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/email/java/com.aspose.email/Pop3MessageInfo#getUniqueId\(\)) para comprobar si un mensaje ya ha sido descargado. El ID único del mensaje debe almacenarse en la base de datos: es la clave de búsqueda para detectar nuevos mensajes.
## **Detectando Nuevos Mensajes**
Para identificar nuevos correos electrónicos de una lista de correos en un servidor POP3:

1. Conéctate al servidor.
1. Obtén una lista de correos electrónicos.
1. Conéctate a la base de datos.
1. Obtén una lista de correos electrónicos.
1. Compara las listas.
1. Guarda nuevos correos electrónicos en la base de datos.

El proceso es más rápido cuando tú:

1. Recuperas todos los IDs únicos de los mensajes en una tabla hash.
1. Buscas en la tabla hash en lugar de en la base de datos para cada mensaje de correo electrónico en un bucle for(…) .

En lugar de consultar la base de datos para cada mensaje, lo que requiere muchas llamadas a la base de datos, este método solo requiere una llamada. El siguiente fragmento de código te muestra cómo detectar mensajes de correo electrónico nuevos en el servidor POP3.

~~~Java
public static void run() {
    try {
        // Conéctate al servidor de correo POP3 y verifica los mensajes.
        Pop3Client pop3Client = new Pop3Client("pop.domain.com", 993, "username", "password");

        // Lista todos los mensajes
        Pop3MessageInfoCollection msgList = pop3Client.listMessages();
        for (Pop3MessageInfo msgInfo : msgList) {
            // Obtén el ID único del mensaje POP3
            String strUniqueID = msgInfo.getUniqueId();

            // Busca en tu base de datos local o almacén de datos por el ID único. Si se encuentra una coincidencia, significa que ya ha sido descargado. De lo contrario, descárgalo y guárdalo.
            if (searchPop3MsgInLocalDB(strUniqueID) == true) {
                // El mensaje ya está en la base de datos. Nada que hacer con este mensaje. Ve al siguiente mensaje.
            } else {
                // Guarda el mensaje
                savePop3MsgInLocalDB(msgInfo);
            }
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }

}

private static void savePop3MsgInLocalDB(Pop3MessageInfo msgInfo) {
    // Abre la conexión a la base de datos de acuerdo a tu base de datos. Usa propiedades públicas (por ejemplo msgInfo.Subject) y almacena en la base de datos,
    // por ejemplo, " INSERT INTO POP3Mails (UniqueID, Subject) VALUES ('" + msgInfo.UniqueID + "' , '" + msgInfo.Subject + "') y ejecuta la consulta para almacenar en la base de datos.
}

private static boolean searchPop3MsgInLocalDB(String strUniqueID) {
    // Abre la conexión a la base de datos de acuerdo a tu base de datos. Usa strUniqueID en la consulta de búsqueda para encontrar registros existentes,
    // por ejemplo, " SELECT COUNT(*) FROM POP3Mails WHERE UniqueID = '" + strUniqueID + "' ejecuta la consulta, devuelve verdadero si count == 1. Devuelve falso si count == 0.
    return false;
}
~~~