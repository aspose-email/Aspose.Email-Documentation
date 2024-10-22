---
title: "Protocolo de Transferência de Correio Simples"
url: /pt/java/simple-mail-transfer-protocol/
weight: 10
type: docs
---

{{% alert color="primary" %}} 

O Protocolo de Transferência de Correio Simples (SMTP) é usado para transferir mensagens de e-mail pela internet. A porta padrão para SMTP é 25. Especificamos um ou mais destinatários, assunto, corpo e outros objetos codificados na mensagem de e-mail. A mensagem é então transferida para um servidor SMTP remoto. O cliente se conecta ao servidor SMTP remoto usando o endereço IP ou nome de domínio na porta 25. A autenticação é realizada com um nome de usuário e senha. O servidor SMTP também pode aceitar conexões anônimas que não exigem autenticação. O servidor então entrega a mensagem aos destinatários em nome do cliente.

- [RFC2821](http://www.rfc-archive.org/getrfc.php?rfc=2821)
- [RFC821](http://www.rfc-archive.org/getrfc.php?rfc=821)

{{% /alert %}}