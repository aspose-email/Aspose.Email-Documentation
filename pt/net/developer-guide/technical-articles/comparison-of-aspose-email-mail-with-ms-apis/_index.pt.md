---
title: "Comparação do Aspose.Email.Mail com APIs da MS"
url: /pt/net/comparison-of-aspose-email-mail-with-ms-apis/
weight: 20
type: docs
---

## **Comparação do Aspose Email Mail com APIs da MS**
System.Web.Mail é simplesmente um wrapper em torno de duas bibliotecas COM: CDONTS.NewMail (encontrada no cdonts.dll) e CDO.Message (encontrada no cdosys.dll). Você também precisará tê-las instaladas em seu servidor. Por padrão, cdonts.dll e cdosys.dll são instaladas com WindowsNT/2000/XP/2003.
### **Especificidades do SmtpMail**
Se você investigar a classe System.Web.Mail.SmtpMail, encontrará alguns comportamentos estranhos:

- Ele suporta apenas sistemas operacionais Win32NT, por exemplo, Windows 2000, Windows 2003, Windows XP.
- Quando a classe SmtpMail envia uma mensagem de e-mail, ela verifica a versão do SO. Se a versão for <= 4, o objeto CDONTS.Newmail é usado; para todos os sistemas operacionais superiores a 4, o objeto CDO.Message é usado.

Essas peculiaridades tornam a resolução de problemas muito mais difícil, especialmente ao mover o código para diferentes sistemas operacionais. A aplicação pode ter resultados inesperados em diferentes SOs. Aspose.Email.Mail é um componente .NET escrito em código totalmente gerenciado em C# puro. Ele não depende de nenhuma biblioteca COM, incluindo CDONTS.NewMail ou CDO.Message. Com Aspose.Email.Mail, você evita invocar qualquer código não gerenciado em suas aplicações, aumentando a confiabilidade e se livrando da chata depuração de COM. Aspose.Email.Mail é rico em recursos e oferece muitos mais serviços do que os fornecidos pela arquitetura System.Web.Mail. System.Net.Mail é uma nova implementação de cliente de protocolo SMTP no .NET 2.0. É também uma implementação de código totalmente gerenciado em C#.
### **Matriz de Comparação**

|**Recursos** |**Aspose.Email.Mail** |**System.Web.Mail** |**System.Net.Mail** |
| :- | :- | :- | :- |
|Recursos de Compatibilidade | | | |
|Suporta .NET 2.0 |X |X |X |
|Recursos Comuns | | | |
|Dependência de CDO/CDONTS | |X | |
|Código Totalmente Gerenciado |X | |X |
|Autenticação |X |X |X |
|Endereço do Remetente |X |X |X |
|Endereços dos Destinatários |X |X |X |
|Corpo HTML |X |X |X |
|Corpo de Texto |X |X |X |
|Bcc/Cc |X |X |X |
|Enviar Anexo |X |X |X |
|Imagem Vinculada |X | |X |
|Codificação do Corpo (Unicode/ASCII) |X |X |X |
|Codificação do Assunto (Unicode/ASCII) |X | |X |
|Modelo de programação síncrona |X | |X |
|Modelo de programação assíncrona |X | |X |
|Recursos Exclusivos | | | |
|Cabeçalho de E-mail Personalizado |X | | |
|Cabeçalho de Importância |X | | |
|Cabeçalho de Sensibilidade |X | | |
|Cabeçalho X-Mailer |X | | |
|Responder a |X | | |
|Data de Envio |X | | |
|Mesclagem de E-mail Baseada em Modelo |X | | |
|Mesclagem de E-mail a partir de DataSet |X | | |
|Mesclagem de E-mail a partir de DataTable |X | | |
|Mesclagem de E-mail a partir de DataReader |X | | |
|Envio em Massa com Multithreading |X | | |
|Enviar Calendário |X | | |
|Enviar solicitação de reunião |X | | |
|Carregar do formato Msg da Microsoft |X | | |
|Carregar do formato Mht da Microsoft |X | | |
|Salvar no formato Mht da Microsoft |X | | |
|Salvar no formato Eml |X | | |
|Carregar do formato Eml |X | | |
|Carregar de arquivo compatível com RFC 822 |X | | |
|Recursos de Interoperabilidade | | | |
|Funciona com Aspose.Email.Pop3 |X | | |
|Funciona com Aspose.Email.Imap |X | | |
|Funciona com Aspose.Email.Mime |X | | |