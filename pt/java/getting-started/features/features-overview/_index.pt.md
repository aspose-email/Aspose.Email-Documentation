---
title: "Visão Geral dos Recursos"
url: /pt/java/features-overview/
weight: 10
type: docs
---

Apose.Email para Java é dividido em vários componentes separados, cada um com características particulares. Aqui está uma lista das características de cada um dos principais pacotes.
## **Aspose.Email.Mail**
### **Características Gerais de Email**
- Criar emails contendo texto simples
- Criar emails contendo HTML
- Criar corpos de mensagem alternativos para compatibilidade com clientes de email que suportam tanto HTML quanto não-HTML
- Conectar-se a qualquer servidor SMTP em uma porta especificada
- Enviar emails através de qualquer servidor SMTP
- Conectar-se a um servidor SMTP habilitado para SSL
- Conectar-se a um servidor SMTP baseado em TLS
### **Características de Anexos**
- Adicionar anexos a emails
- Remover anexos de emails
- Criar anexos a partir de caminhos de arquivos
- Criar anexos a partir de streams
- Criar anexos a partir de arrays de bytes
### **Características de Objetos Incorporados**
- Incorporar objetos (como imagens, sons e assim por diante) nos seus emails
- Remover objetos incorporados dos seus emails
- Incorporar objetos a partir de caminhos de arquivos
- Incorporar objetos a partir de streams
- Incorporar objetos a partir de arrays de bytes
### **Características de Importação/Exportação**
- Importar emails no formato Microsoft Outlook Email Message (MSG).
- Importar emails no formato Microsoft HTML (MHT)
- Importar emails no formato de mensagem compatível com RFC822 (EML)
- Criar emails a partir de conteúdos HTML
- Exportar emails para o formato Microsoft HTML (MHT)
- Exportar emails para o formato de mensagem compatível com RFC822 (EML)
- Exportar emails de um arquivo PST do Outlook para arquivos MSG do Outlook
### **Características de Email em Massa**
- Suporta o envio de emails em lotes
- Recurso de multi-threading embutido para envio de emails em massa
- Suporta salvar mensagens de email em massa em um pool de mensagens
### **Características de Mala Direta**
- Mala direta baseada em modelos usando diferentes fontes de dados
- Suporta DataTable como fonte de dados
- Suporta DataRowCollection como fonte de dados
- Suporta DataReader como fonte de dados
- Criar modelo de email a partir de um arquivo
- Criar modelo de email a partir de uma instância de MailMessage
- Realizar mala direta linha a linha para gerar mensagens de email
### **Características de Calendário**
- Adicionar eventos iCalendar a mensagens de email.
- Cancelar eventos iCalendar.
- Enviar solicitações de reunião por email.
- Enviar solicitações de compromisso por email.
### **Características de Manipulação de Eventos**
- Suporta uma variedade de eventos úteis para fornecer mais controle.
- Realizar ações quando todos os emails em massa forem enviados.
- Realizar ações quando uma mensagem estiver prestes a ser enviada.
- Ser notificado através de um evento quando um email for completamente enviado.
### **Características de Utilitário**
- Personalizar cabeçalhos de email.
- Definir prioridade, data e hora da mensagem.
- Suporta todos os conjuntos de caracteres.
- Solicitar recibos de leitura.
### **Características Avançadas**
- Modelos de programação assíncrona e síncrona.
- Suporta análise de emails nos formatos MSG, MHT e EML.
- Suporta salvar emails nos formatos MSG, MHT e EML.
- Extrair anexos de arquivos de Mensagem de Email do Microsoft Outlook (MSG).
- Ler mensagens de arquivos PST do Outlook.
- Suporta conexão SMTP de backup.
- Especificar o número de tentativas para conexões SMTP.
## **Aspose.Email.Mime**
{{% alert %}}
**Experimente!**

Analise arquivos de email com o gratuito [**Aspose.Email Parser App**](https://products.aspose.app/email/pt/parser).
{{% /alert %}}
### **Características Gerais de Análise**
- Extrair cabeçalhos de email e corpos de mensagens.
- Recuperar nomes e valores dos cabeçalhos de email.
- Recuperar endereços From, To, Cc e Reply-To.
- Recuperar e salvar anexos.
- Recuperar e salvar objetos incorporados como imagens e sons.
### **Características de Importação/Exportação**
- Importar emails no formato Microsoft Outlook Email Message (MSG).
- Importar emails no formato Microsoft HTML (MHT).
- Importar emails no formato de mensagem compatível com RFC822 (EML).
- Exportar emails para o formato Microsoft HTML (MHT).
- Exportar emails para o formato de mensagem compatível com RFC822 (EML).
### **Características de Utilitário**
- Suporta múltiplos cabeçalhos.
- Suporta múltiplas partes.
- Suporta todos os conjuntos de caracteres.
- Recuperar metadados como contentType, MimeVersion e XMailer.

{{% alert %}}
**Experimente!**

Use [**Aspose.Email Metadata App**](https://products.aspose.app/email/pt/metadata) para visualizar e editar metadados online, propriedades embutidas ou propriedades personalizadas da mensagem.
{{% /alert %}}
### **Características Avançadas de Análise**
- Carregar e analisar emails nos formatos MSG, MHT e EML.
## **Aspose.Email.Pop3**
### **Características Gerais de POP3**
- Recuperar mensagens completas ou apenas cabeçalhos.
- Suporta comandos POP3 básicos.
- Listar mensagens de email.
- Recuperar emails nos formatos MIME e texto simples.
- Recuperar informações da caixa de correio.
- Manter a conexão POP3 ativa.
- Recursos de gerenciamento de email.
- Excluir emails selecionados no servidor POP3.
- Excluir todos os emails.
- Cancelar exclusão no servidor POP3.
- Conectar-se a um servidor POP3 habilitado para SSL.
### **Características de Segurança**
- Suporta Protocolo de Post Office Autenticado (APOP).
- Suporta autenticação Clear Text USER/PASS.
- Suporta autenticação CRAM-MD5 conforme RFC 2195.
- Suporta autenticação DIGEST-MD5 conforme RFC 2831.
- Suporta autenticação de login.
- Suporta autenticação em texto claro TLS conforme RFC 2595.
## **Aspose.Email.Exchange**
### **Características Gerais de Exchange**
- Conectar-se ao Microsoft Exchange Server 2003, 2007, 2010 e 2013.
- Recuperar emails do Exchange Server.
- Listar mensagens de email.
- Recuperar informações da caixa de correio.
- Recursos de gerenciamento de email.
- Excluir emails selecionados no Exchange Server.
## **Características de Utilitário**
- Definir timeouts de conexão e leitura.
- Definir tamanho de buffer para enviar e receber.
- Obter identificadores únicos de emails em um servidor.
- Recuperar contagem de mensagens.
- Recuperar tamanho da mensagem.
## **Aspose.Email.Imap**
### **Características Gerais**
- Conectar e comunicar-se com servidores IMAP.
- Manipular mensagens de email e pastas no servidor.
- Conectar-se a um servidor IMAP habilitado para SSL.
- Ser notificado quando um email é recebido, evitando assim a verificação repetida do servidor.
### **Características de Gerenciamento de Mensagens**
- Buscar mensagens de email.
- Buscar cabeçalhos de mensagens de email.
- Salvar mensagens de email no sistema de arquivos local.
- Excluir mensagens de email.
- Listar mensagens de email na pasta especificada.
- Definir flags (lido, excluído e assim por diante) para mensagens de email específicas.
### **Características de Gerenciamento de Pastas**
- Criar pastas de email.
- Excluir pastas de email.
- Renomear pastas de email.
### **Características de Segurança**
- Suporta autenticação Clear Text USER/PASS.
- Suporta autenticação CRAM-MD5 conforme RFC 2195.
- Suporta autenticação DIGEST-MD5 conforme RFC 2831.
- Suporta autenticação de login.
- Suporta autenticação em texto claro TLS conforme RFC 2595.
## **Aspose.Email.Verify**
### **Características de Validação**
- Validar endereços de email.
- Suporta validação de sintaxe de email.
- Suporta validação de domínio de email.
- Suporta validação de servidor de email.
- Suporta validação de registros MX.
- Validação assíncrona.
- Resultados de validação flexíveis.
### **Características de Utilitário**
- Especificar servidores DNS.* Definir timeout de solicitação.
## **Aspose.iCalendar**
- Calcular facilmente e de forma confiável datas e horários de ocorrência mesmo para os padrões de recorrência mais complexos.
- Consumir e produzir padrões de recorrência no formato iCalendar (RFC 2445).
- Criar padrões de recorrência programaticamente através de um modelo de objeto intuitivo.
- Usar padrões de recorrência anuais, mensais, semanais, diários, horários, a cada minuto e a cada segundo.
- Representar padrões de recorrência em suas aplicações de desktop, web ou móveis.
## **Suporte a Arquivos PST/OST**
- Suporte a arquivos de Armazenamento Pessoal e Offline
- Gerar e ler arquivos OST, PST
- Suporta arquivos PST de todos os tipos
- Todos os tipos de OST suportados para leitura
## **Protocolos Suportados**
- SMTP
- MIME
- POP3
- IMAP
- HTTP