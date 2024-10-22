---
title: "FAQs"
url: /pt/java/faqs/
weight: 220
type: docs
---

**Pergunta**

Olá! para o seguinte código:

~~~Java

ContentType ct = new ContentType();

ct.setMediaType("application/msword");

ct.setCharSet("ISO-2022-JP");

Attachment att = new Attachment("Test.doc", ct);

System.out.println(att.getContentType().getName());

~~~

att.getContentType().getName() retorna o nome do documento anexado. Comportamento esperado é esse?

**Resposta**: 
Sim, é um comportamento esperado. Se getContentType().getName() não for definido explicitamente, o valor do nome do arquivo será considerado como um nome.

**Pergunta:** 
Como posso extrair dados do anexo "oleData.mso" que recebo como resultado da leitura de um MapiMessage contendo um objeto OLE incorporado?

**Resposta**: 
Arquivos como "oleData.mso" referem-se ao formato de arquivo Microsoft Compound Document (MCDF) e, infelizmente, o suporte para tais arquivos está além da ocupação do Aspose.Email. No entanto, existem certas bibliotecas .NET de código aberto, como OpenMCDF, que podem ser usadas para ler o conteúdo de tais arquivos para salvá-los em disco.

**Pergunta:** 
Podemos escrever no mesmo arquivo PST em threads paralelas usando os mesmos objetos?

**Resposta:** 
Não, a segurança da thread não é garantida nesse caso. A gravação de mensagens deve ser feita em uma única thread. No entanto, o produto deve funcionar corretamente com diferentes objetos de diferentes threads.