---
title: "Protocolo Simple de Transferencia de Correo"
url: /es/java/simple-mail-transfer-protocol/
weight: 10
type: docs
---

{{% alert color="primary" %}} 

El Protocolo Simple de Transferencia de Correo (SMTP) se utiliza para transferir mensajes de correo electrónico a través de Internet. El puerto predeterminado para SMTP es el 25. Especificamos uno o más destinatarios, asunto, cuerpo y otros objetos codificados en el mensaje de correo electrónico. El mensaje se transfiere a un servidor SMTP remoto. El cliente se conecta al servidor SMTP remoto utilizando la dirección IP o el nombre de dominio en el puerto 25. La autenticación se realiza con un nombre de usuario y una contraseña. El servidor SMTP también puede aceptar conexiones anónimas que no requieren autenticación. El servidor luego entrega el mensaje a los destinatarios en nombre del cliente.

- [RFC2821](http://www.rfc-archive.org/getrfc.php?rfc=2821)
- [RFC821](http://www.rfc-archive.org/getrfc.php?rfc=821)

{{% /alert %}}