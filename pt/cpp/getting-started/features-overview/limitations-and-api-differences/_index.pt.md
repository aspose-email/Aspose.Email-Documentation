---
title: "Limitações e Diferenças da API"
description: "A biblioteca C++ Email Parser tem algumas diferenças em comparação com sua versão equivalente .NET. Esta página contém informações sobre toda a funcionalidade que não está disponível na API."
url: /pt/cpp/limitações-e-diferenças-da-api/
weight: 10
type: docs
---

Aspose.Email para C++ tem algumas diferenças em comparação com sua versão equivalente .NET da API. Esta página contém informações sobre toda a funcionalidade que não está disponível na API.
## **Limitações da API**
Aspose.Email para C++ tem as seguintes limitações que o diferenciam de outras APIs da família de produtos Aspose.Email. Estas são:

- No momento, a API suporta os seguintes protocolos de comunicação:
  - SMTP
  - POP3
  - IMAP
- A API não suporta Exchange (WebDav e EWS)
- Sem suporte para formatos de arquivos Thunderbird MBox
- Não oferece suporte para Criptografia/Descriptografia de Mensagens
- O suporte para conversão de MapiMessage para MailMessage também não está presente
- Receber notificações e Confirmações de Leitura
- Criar emails TNEF a partir de arquivos MSG
- Detectar tipo de mensagem também não é suportado
- Trabalhar com recorrências, incluindo EndAfterNoccurrences, WeeklyEndAfterNoccurrences, EndAfterNoccurrenceSelectMultipleDaysInweek, MonthlyEndAfterNoccurrences
- Detectar Mensagem como TNEF
- Detectar mensagem incorporada usando a flag Embeddedd
- Remover Recursos Vinculados em local específico
- Renderizar eventos de calendário com base em templates de formato
- Excluir itens filhos de pastas de arquivos PST
- Alterar propriedades da mensagem na Pasta do PST usando ChangeMessages