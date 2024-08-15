---
title: "Protocolo simple de transferencia de correo"
url: /es/java/simple-mail-transfer-protocol/
weight: 10
type: docs
---

{{% alert color="primary" %}}

El Protocolo simple de transferencia de correo (SMTP) se usa para transferir mensajes de correo electrónico a través de Internet. El puerto predeterminado para SMTP es 25. Especificamos uno o más destinatarios, el asunto, el cuerpo y otros objetos codificados en el mensaje de correo electrónico. A continuación, el mensaje se transfiere a un servidor SMTP remoto. El cliente se conecta al servidor SMTP remoto mediante la dirección IP o el nombre de dominio del puerto 25. La autenticación se realiza con un nombre de usuario y una contraseña. El servidor SMTP también puede aceptar conexiones anónimas que no requieren autenticación. A continuación, el servidor entrega el mensaje a los destinatarios en nombre del cliente.

- [RFC2821](http://www.rfc-archive.org/getrfc.php?rfc=2821)
- [RFC821](http://www.rfc-archive.org/getrfc.php?rfc=821)

{{% /alert %}}
