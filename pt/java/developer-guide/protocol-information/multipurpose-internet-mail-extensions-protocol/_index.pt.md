---
title: "Protocolo de Extensões de Correio da Internet Multifunção"
url: /pt/java/protocolo-de-extensoes-de-correio-da-internet-multifunção/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

As Extensões de Correio da Internet Multifunção (MIME) são um padrão da Internet que estende o formato de email para suportar:

- texto em conjuntos de caracteres diferentes de US-ASCII;
- anexos que não são texto;
- corpos de mensagem multipartes; e
- informações de cabeçalho em conjuntos de caracteres não ASCII.

O SMTP suporta apenas caracteres ASCII de 7 bits, o que significa efetivamente que ele suporta apenas um pequeno número de idiomas. Idiomas baseados no alfabeto latino funcionam bem no SMTP; outros idiomas não são exibidos corretamente quando o email é entregue. O MIME, no entanto, estende o suporte a caracteres ASCII do SMTP para que emails usando outros conjuntos de caracteres, imagens e sons possam ser enviados e exibidos. Geralmente, todos os clientes de email e servidores SMTP mapeiam corretamente mensagens no formato MIME. 

{{% /alert %}} 
## **Entendendo os Cabeçalhos MIME**
Os cabeçalhos MIME contêm informações sobre o protocolo.
### **MIME-Version**
Isso indica que a mensagem está formatada em MIME. Aparece como:

MIME-Version: 1.0
### **Content-Type**
Isso indica o tipo de conteúdo da mensagem, apresentado como um par de tipo e subtipo: text/plain, text/html, por exemplo. O tipo de conteúdo multipart pode conter texto, HTML, anexos, imagens, áudio, vídeo e assim por diante. 

Content-Type: multipart
### **Content-Transfer-Encoding**
Indica se um esquema de codificação binário-para-texto é utilizado em cima da codificação especificada por content-type. Se sim, indica qual. Podemos especificar tipos de codificação de 7 bits, 8 bits e binário aqui. 
### **Encoded-Word**
Os cabeçalhos de mensagens SMTP normalmente usam caracteres ASCII. Caracteres não-ASCII devem usar a sintaxe de palavra codificada MIME em vez de uma string literal. O formato é: 

"=? *charset* ? *encoding* ? *texto codificado* ?=". 
### **Multipart-Messages**
Uma mensagem multipart MIME contém um limite no cabeçalho do tipo de conteúdo. Este limite, que não deve ocorrer em nenhuma das partes, é colocado entre as partes e no início e no final do corpo da mensagem, da seguinte forma:

**MIME-version: 1.0**

~~~Java

 Content-type: multipart/mixed; boundary="frontier"

Esta é uma mensagem multipart no formato MIME.

--frontier

Content-type: text/plain

Este é o corpo da mensagem.

--frontier

Content-type: application/octet-stream

Content-transfer-encoding: base64

PGh0bWw+CiAgPGhlYWQ+CiAgPC9oZWFkPgogIDxib2R5PgogICAgPHA+VGhpcyBpcyB0aGUg

Ym9keSBvZiB0aGUgbWVzc2FnZS48L3A+CiAgPC9ib2R5Pgo8L2h0bWw+Cg==

--frontier--

~~~

Cada parte consiste em seu próprio cabeçalho de conteúdo e um corpo. 
### **Subtipos Multipart**
O padrão MIME define vários subtipos de mensagem multipart. O subtipo é especificado no cabeçalho "Content-Type" da mensagem geral.

A seguir, está uma lista dos subtipos mais comumente usados.

- Mixed: Multipart/mixed é usado para enviar arquivos com diferentes cabeçalhos "Content-Type" em linha. Ao enviar imagens ou outros arquivos de fácil leitura, a maioria dos clientes de email os exibirá em linha.
- Message: Uma parte de mensagem contém uma mensagem de email.
- Digest: digest é uma maneira simples de enviar várias mensagens de texto. O tipo de conteúdo padrão para cada parte é "message/rfc822".
- Alternative: O subtipo alternative indica que cada parte é uma versão "alternativa" do mesmo (ou similar) conteúdo, cada uma em um formato diferente denotado por seu cabeçalho "Content-Type".

O multipart/alternative é mais comumente usado para emails com duas partes, uma em texto simples (text/plain) e outra em HTML (text/html). A parte em texto simples fornece compatibilidade retroativa, enquanto a parte em HTML permite o uso de formatação e hiperlinks. A maioria dos clientes de email oferece uma opção para o usuário preferir texto simples em vez de HTML; este é um exemplo de como fatores locais podem afetar como um aplicativo escolhe qual parte "melhor" da mensagem exibir. 

{{% alert color="primary" %}} 

Para mais informações, siga esses links para os arquivos RFC.

- [RFC2045](https://www.rfc-archive.org/getrfc.php?rfc=2045#gsc.tab=0)
- [RFC131](https://www.rfc-archive.org/getrfc.php?rfc=131#gsc.tab=0)

{{% /alert %}}