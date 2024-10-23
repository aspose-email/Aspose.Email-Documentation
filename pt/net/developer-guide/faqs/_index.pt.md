---
title: "FAQs"
url: /pt/net/faqs/
weight: 210
type: docs
---

**Pergunta**

Olá! para o seguinte código:

``` java

 Aspose.Email.Mime.ContentType ct = new Aspose.Email.Mime.ContentType();

ct.MediaType = "application/msword";

ct.CharSet = "ISO-2022-JP";

Attachment att = new Attachment("Test.doc", ct);

Console.WriteLine(att.ContentType.Name);

```

att.ContentType.Name retorna o nome do documento anexado. Isso é um comportamento esperado?

**Resposta**: 
Sim, é um comportamento esperado. Se ContentType.Name não for definido explicitamente, o valor do nome do arquivo será considerado como o nome.

**Pergunta:**

Por que o ExchangeWebServiceClient.FetchMessage faz com que as imagens embutidas sejam anexos?

**Resposta**: 
O Microsoft Exchange Server possui uma funcionalidade como '[Conversão de Conteúdo](http://technet.microsoft.com/en-us/library/bb232174\(EXCHG.80\).aspx), que é o processo de formatar corretamente uma mensagem para cada destinatário. A decisão de realizar a conversão de conteúdo em uma mensagem depende do destino e do formato da mensagem que está sendo processada.

Em outras palavras, para clientes desconhecidos, o servidor pode realizar a formatação da mensagem de acordo com as configurações do servidor (para selecionar o formato de mensagem mais apropriado). Como você entende, o formato mais universal para qualquer cliente é 'text/plain' e essas configurações são configuráveis no servidor.

Por favor, note: O Outlook é um cliente de e-mail bem conhecido para o Microsoft Exchange Server (caso o MS Outlook tenha uma versão mais antiga que o servidor). Isso significa que o Exchange Server passa o formato da mensagem de acordo com as capacidades do Outlook. No nosso caso, quando o ExchangeWebServiceClient tenta recuperar a mensagem, as capacidades dos nossos componentes são desconhecidas para o MS Exchange. O servidor passa a mensagem para os componentes no formato mais simples (text/plain). Em outras palavras, não há partes html na resposta do servidor. Nessa situação, as imagens estão incluídas na mensagem como anexos.

Há uma maneira de evitar o problema descrito. Se a mensagem no servidor tiver Content-Type: multipart/alternative e uma de suas partes for text/plain, nesse caso essa mensagem passa para o cliente como está. As imagens nesse caso são exibidas no corpo da mensagem porque a mensagem também contém a parte html. No cenário atual, a mensagem é adicionada ao MS Exchange com a ajuda do MS Outlook e, como resultado, o Content-Type da mensagem não é 'multipart/alternative'. Como resultado, temos um problema quando tentamos buscar a mensagem. Por exemplo, aqui estão amostras de problemas semelhantes: um(<http://support.risualblogs.com/blog/2011/02/24/html-mails-sent-via-owa-and-outlook-2011-are-received-as-plain-text-mails-externally/>), dois(<http://forums.mozillazine.org/viewtopic.php?f=39&t=628678>), três(<http://stackoverflow.com/questions/4681798/how-do-i-send-html-multipart-alternative-from-exchange-web-services-2010-sp1)Como> conclusão, a situação descrita na questão (imagens incluídas na mensagem como anexos) não é um erro dos componentes Aspose. Esta é uma característica específica do servidor Exchange.

**Pergunta:** 
Como posso extrair dados do anexo "oleData.mso" que recebo como resultado da leitura de um MapiMessage que tem um objeto OLE embutido nele?

**Resposta**: 
Arquivos como "oleData.mso" referem-se ao formato de arquivo Microsoft Compound Document (MCDF) e, infelizmente, o suporte para tais arquivos está além da ocupação do Aspose.Email. No entanto, existem certas bibliotecas .NET de código aberto, por exemplo, OpenMCDF, que podem ser usadas para ler o conteúdo desses arquivos para salvar em disco.

**Pergunta:** 
Podemos escrever no mesmo arquivo PST em threads paralelas usando os mesmos objetos?

**Resposta:** 
Não, a segurança da thread não é garantida nesse caso. A escrita de mensagens deve ser feita em uma única thread. No entanto, o produto deve funcionar corretamente com diferentes objetos de diferentes threads.