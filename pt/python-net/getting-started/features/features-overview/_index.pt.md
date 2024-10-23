---
title: "Visão Geral das Funcionalidades"
url: /pt/python-net/features-overview/
weight: 10
type: docs
---

Apose.Email para Python via .NET é dividido em vários componentes separados, cada um com características particulares. Aqui está uma lista das funcionalidades de cada um dos principais pacotes.
## **Aspose.Email.Mail**
### **Funcionalidades Gerais de Email**
- Criar emails contendo texto simples
- Criar emails contendo HTML
- Criar corpos de mensagem alternativos para compatibilidade com clientes de email que suportam HTML e não HTML
- Conectar-se a qualquer servidor SMTP em uma porta especificada
- Enviar emails através de qualquer servidor SMTP
- Conectar-se a servidor SMTP habilitado para SSL
- Conectar-se a servidor SMTP baseado em TLS
### **Funcionalidades de Anexo**
- Adicionar anexos aos seus emails
- Remover anexos dos seus emails
- Criar anexos a partir de caminhos de arquivo
### **Funcionalidades de Objetos Incorporados**
- Incorporar objetos (como imagens, sons e assim por diante) em seus emails.
- Remover objetos incorporados de seus emails.
- Incorporar objetos a partir de caminhos de arquivo.
- Incorporar objetos a partir de streams.
- Incorporar objetos a partir de arrays de bytes.
### **Funcionalidades de Importação/Exportação**
- Importar emails no formato Microsoft Outlook Email Message Format (MSG).
- Importar emails no formato Microsoft HTML (MHT)
- Importar emails no formato de mensagem compatível com RFC822 (EML)
- Criar emails a partir de conteúdos HTML
- Exportar emails para o formato Microsoft HTML (MHT)
- Exportar emails para o formato de mensagem compatível com RFC822 (EML)
- Exportar emails de um arquivo PST do Outlook para arquivos MSG do Outlook
### **Funcionalidades de Email em Massa**
- Suporta o envio de emails em lotes.
- Recurso de multi-threading integrado para envio de emails em massa.
- Suporta salvar mensagens de email em massa em um pool de mensagens
### **Funcionalidades de Calendário**
- Adicionar eventos iCalendar a mensagens de email.
- Cancelar eventos iCalendar.
- Enviar solicitações de reunião por email.
- Enviar solicitações de compromisso por email.
### **Funcionalidades de Utilitários**
- Personalizar cabeçalhos de email.
- Definir prioridade, data e hora da mensagem.
- Suporta todos os conjuntos de caracteres.
- Solicitar recibos de leitura.
### **Funcionalidades Avançadas**
- Modelos de programação assíncronos e síncronos.
- Suporta o parsing de emails nos formatos MSG, MHT e EML.
- Suporta o salvamento de emails nos formatos MSG, MHT e EML.
- Extrair anexos de arquivos Microsoft Outlook Email Message (MSG).
- Ler mensagens de arquivos PST do Outlook.
- Suporta conexão SMTP de backup.
- Especificar o número de tentativas para conexões SMTP.
## **Aspose.Email.Mime**
{{% alert %}}
**Experimente!**

Analise arquivos de email com o gratuito [**Aspose.Email Parser App**](https://products.aspose.app/email/pt/parser).
{{% /alert %}}
### **Funcionalidades Gerais de Parsing**
- Extrair cabeçalhos de email e corpos de mensagem.
- Recuperar nomes e valores dos cabeçalhos de email.
- Recuperar endereços From, To, Cc e Reply-To.
- Recuperar e salvar anexos.
- Recuperar e salvar objetos incorporados como imagens e sons.
### **Funcionalidades de Importação/Exportação**
- Importar emails no formato Microsoft Outlook Email Message (MSG).
- Importar emails no formato Microsoft HTML (MHT).
- Importar emails no formato de mensagem compatível com RFC822 (EML).
- Exportar emails para o formato Microsoft HTML (MHT).
- Exportar emails para o formato de mensagem compatível com RFC822 (EML).
### **Funcionalidades de Utilitários**
- Suporta múltiplos cabeçalhos.
- Suporta múltiplas partes.
- Suporta todos os conjuntos de caracteres.
- Recuperar metadados como contentType, MimeVersion e XMailer.

{{% alert %}}
**Experimente!**

Use [**Aspose.Email Metadata App**](https://products.aspose.app/email/pt/metadata) para visualizar e editar metadados online, propriedades integradas ou propriedades personalizadas da mensagem.
{{% /alert %}}
### **Funcionalidades Avançadas de Parsing**
- Carregar e analisar emails nos formatos MSG, MHT e EML.
## **Aspose.Email.Pop3**
### **Funcionalidades Gerais do POP3**
- Recuperar mensagens completas ou apenas cabeçalhos.
- Suporta comandos básicos do POP3.
- Listar mensagens de email.
- Recuperar emails nos formatos MIME e texto simples.
- Recuperar informações da caixa de correio.
- Manter a conexão POP3 ativa.
- Funcionalidades de gerenciamento de email.
- Excluir emails selecionados no servidor POP3.
- Excluir todos os emails.
- Cancelar exclusão no servidor POP3.
- Conectar-se a servidor POP3 habilitado para SSL.
### **Funcionalidades de Segurança**
- Suporta Protocolo de Correio Autenticado (APOP).
- Suporta autenticação de texto claro USER/PASS.
- Suporta autenticação CRAM-MD5 de acordo com RFC 2195.
- Suporta autenticação DIGEST-MD5 de acordo com RFC 2831.
- Suporta autenticação de login.
- Suporta autenticação de texto claro TLS de acordo com RFC 2595.
## **Aspose.Email.Imap**
### **Funcionalidades Gerais**
- Conectar e se comunicar com servidores IMAP.
- Manipular mensagens de email e pastas no servidor.
- Conectar-se a servidor IMAP habilitado para SSL.
- Receber notificação quando um email é recebido, evitando assim a verificação repetida do servidor.
### **Funcionalidades de Gerenciamento de Mensagens**
- Buscar mensagens de email.
- Buscar cabeçalhos de mensagens de email.
- Salvar mensagens de email no sistema de arquivos local.
- Excluir mensagens de email.
- Listar mensagens de email na pasta especificada.
- Definir flags (lido, excluir e assim por diante) para mensagens de email especificadas.
### **Funcionalidades de Gerenciamento de Pastas**
- Criar pastas de email.
- Excluir pastas de email.
- Renomear pastas de email.
### **Funcionalidades de Segurança**
- Suporta autenticação de texto claro USER/PASS.
- Suporta autenticação CRAM-MD5 de acordo com RFC 2195.
- Suporta autenticação DIGEST-MD5 de acordo com RFC 2831.
- Suporta autenticação de login.
- Suporta autenticação de texto claro TLS de acordo com RFC 2595.
## **Aspose.iCalendar**
- Calcule facilmente e de forma confiável datas e horários de ocorrência, mesmo para os padrões de recorrência mais complexos.
- Consumir e produzir padrões de recorrência no formato iCalendar (RFC 2445).
- Criar padrões de recorrência programaticamente por meio de um modelo de objeto intuitivo.
- Usar padrões de recorrência anuais, mensais, semanais, diários, horários, a cada minuto e a cada segundo.
- Representar padrões de recorrência em suas janelas, aplicativo web ou móvel.
### **Protocolos Suportados**
- SMTP
- MIME
- POP3
- IMAP
- HTTP
## **Suporte a Arquivos PST/OST**
- Suporte a arquivos de Armazenamento Pessoal e Offline
- Gerar e ler arquivos OST, PST
- Suporta arquivos PST de todos os tipos
- Todos os tipos de OST suportados para leitura