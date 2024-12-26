---
title: Multipurpose Internet Mail Extensions Protocol
ArticleTitle: Multipurpose Internet Mail Extensions Protocol
type: docs
weight: 20
url: /java/multipurpose-internet-mail-extensions-protocol/
---


{{% alert color="primary" %}} 

Multipurpose Internet Mail Extensions (MIME) is an Internet standard that extends the email format to support:

- text in character sets other than US-ASCII;
- non-text attachments;
- multi-part message bodies; and
- header information in non-ASCII character sets.

SMTP supports only 7 bit ASCII characters which effectively means that it only supports a small number of languages. Languages based on the Latin alphabet are fine in SMTP; other languages are not displayed correctly when the email is delivered. MIME, however, extends the ASCII character support of SMPT so that emails using other character sets, images and sounds can be sent and displayed. Generally, all email clients and SMTP servers correctly map messages of MIME format. 

{{% /alert %}} 
## **Understanding MIME Headers**
MIME headers contain information about the protocol.
### **MIME-Version**
This indicates that the message is MIME-formatted. It appears as:

MIME-Version: 1.0
### **Content-Type**
This indicates the content type of the message, given as a type and subtype pair: text/plain, text/html, for example. The multipart content type can contain text, HTML, attachments, images, audio, video and so on. 

Content-Type: multipart
### **Content-Transfer-Encoding**
Indicates whether a binary-to-text encoding scheme is used on top on top of the enciding specified by content-type. If it has, states which one. We can specify 7-bit, 8-bit and binary coding type here. 
### **Encoded-Word**
SMTP messages headers normally use ASCII characters. Non-ASCII characters must use MIME encoded word syntax instead of a literal string. The format is: 

"=? *charset* ? *encoding* ? *encoded text* ?=". 
### **Multipart-Messages**
A MIME multipart message contains a boundary in the content-type header. This boundary, which must not occur in any of the parts, is placed between the parts, and at the beginning and end of the body of the message, as follows:

**MIME-version: 1.0**

~~~Java

 Content-type: multipart/mixed; boundary="frontier"

This is a multi-part message in MIME format.

--frontier

Content-type: text/plain

This is the body of the message.

--frontier

Content-type: application/octet-stream

Content-transfer-encoding: base64

PGh0bWw+CiAgPGhlYWQ+CiAgPC9oZWFkPgogIDxib2R5PgogICAgPHA+VGhpcyBpcyB0aGUg

Ym9keSBvZiB0aGUgbWVzc2FnZS48L3A+CiAgPC9ib2R5Pgo8L2h0bWw+Cg==

--frontier--

~~~

Each part consists of its own content header and a body. 
### **Multipart Subtypes**
The MIME standard defines various multipart-message subtypes. The subtype is specified in the "Content-Type" header of the overall message.

The following is a list of the most commonly used subtypes.

- Mixed: Multipart/mixed is used for sending files with different "Content-Type" headers inline. If sending pictures or other easily readable files, most mail clients will display them inline.
- Message:A message part contains an email message.
- Digest: digest is a simple way to send multiple text messages. The default content-type for each part is "message/rfc822".
- Alternative:The alternative subtype indicates that each part is an "alternative" version of the same (or similar) content, each in a different format denoted by its "Content-Type" header.

Most commonly multipart/alternative is used for email with two parts, one plain text (text/plain) and one HTML (text/html). The plain text part provides backwards compatibility while the HTML part allows use of formatting and hyperlinks. Most email clients offer a user option to prefer plain text over HTML; this is an example of how local factors may affect how an application chooses which "best" part of the message to display. 

{{% alert color="primary" %}} 

For more information, follow these links to the RFC archives.

- [RFC2045](https://www.rfc-archive.org/getrfc.php?rfc=2045#gsc.tab=0)
- [RFC131](https://www.rfc-archive.org/getrfc.php?rfc=131#gsc.tab=0)

{{% /alert %}}
