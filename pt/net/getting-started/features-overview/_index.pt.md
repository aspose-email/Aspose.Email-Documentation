---
title: "features-overview"
url: /pt/net/features-overview/
weight: 25
type: docs
---

No Aspose.Email para .NET, um conjunto diversificado de classes e métodos é  
categorizado em namespaces, cada um servindo a propósitos distintos relacionados ao processamento de emails. Desde o manuseio de protocolos de email como SMTP, POP3 e IMAP até a gestão de tarefas como integrações de calendário e agendamento de tarefas, cada namespace é criado para abordar casos de uso específicos. Essa abordagem estruturada não só simplifica a codificação, mas também garante que os desenvolvedores possam implementar soluções de email com facilidade.

Abaixo, iremos nos aprofundar nos vários namespaces fornecidos pelo Aspose.Email para .NET, explorando suas funções principais e referindo-se às classes mais importantes.

## Aspose.Email: Contém classes comuns para lidar com vários aspectos das mensagens de email

O componente central deste namespace é a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), uma entidade versátil e poderosa que facilita a criação, manipulação e processamento de mensagens de email. A classe MailMessage suporta uma ampla gama de recursos, incluindo compor emails com formatação de texto rica, incorporar imagens, anexar arquivos e especificar múltiplos destinatários com diferentes papéis (para, cc, bcc). Ela também fornece funcionalidades robustas para analisar e ler mensagens de email recebidas, permitindo que os desenvolvedores extraiam detalhes como assunto, remetente, destinatários e conteúdo da mensagem de maneira harmoniosa. Além disso, a MailMessage integra-se suavemente com vários protocolos de email como SMTP, IMAP e POP3, garantindo que enviar e receber emails seja tanto simples quanto confiável.

## Aspose.Email.Amp: Fornece classes para lidar com mensagens com corpo AMP HTML

[Aspose.Email.Amp](https://reference.aspose.com/email/net/aspose.email.amp/) oferece um conjunto robusto de classes dedicadas ao manuseio de mensagens que incluem corpos AMP HTML, tornando-se uma ferramenta para desenvolvedores que desejam incorporar conteúdo de email dinâmico e interativo. No coração dessa capacidade está a classe [AmpMessage](https://reference.aspose.com/email/net/aspose.email.amp/ampmessage/#ampmessage-class), que serve como o componente principal para construir, manipular e renderizar mensagens de email infundidas com AMP. Esta classe permite que os desenvolvedores integrem facilmente mídia rica e elementos interativos diretamente no corpo de um email, aproveitando a velocidade e os recursos envolventes do AMP HTML.

Com o AmpMessage, você pode adicionar elementos como carrosseis de imagens, busca de dados em tempo real e formulários interativos, todos projetados para funcionar de maneira eficiente dentro de um cliente de email.

## Aspose.Email.AntiSpam: Oferece classes para implementar filtros auto-aprendizes para detectar emails de spam

[Aspose.Email.AntiSpam](https://reference.aspose.com/email/net/aspose.email.antispam/) oferece uma solução para filtragem de emails com sua classe central [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) projetada para detectar emails de spam usando um filtro bayesiano auto-aprendente. Esta classe permite que aplicativos analisem e classifiquem emails recebidos como spam ou não, com base em estatísticas bayesianas. O SpamAnalyzer pode aprender com a entrada do usuário, permitindo que melhore sua precisão ao longo do tempo ajustando seu modelo interno com base em emails previamente classificados.

## Aspose.Email.Bounce: Fornece classes para lidar com mensagens de retorno

[Aspose.Email.Bounce](https://reference.aspose.com/email/net/aspose.email.bounce/) oferece uma solução abrangente para aplicativos de email gerenciarem eficientemente mensagens de retorno. A classe [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/#bounceresult-class) representa o resultado da análise da mensagem como uma mensagem de retorno.

## Aspose.Email.Calendar: Contém classes para trabalhar com calendários

[Aspose.Email.Calendar](https://reference.aspose.com/email/net/aspose.email.calendar/) é um namespace projetado para capacitar desenvolvedores com ferramentas para gerenciar e manipular dados de calendário. A classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) encapsula funcionalidades para lidar com eventos e compromissos de calendário. Com a classe Appointment, os desenvolvedores podem criar, modificar e gerenciar eventos de calendário sem esforço, incluindo definir horários de início e término, padrões de recorrência, lembretes e convidar participantes. A classe suporta o formato iCalendar (ICS), garantindo compatibilidade e integração com diferentes sistemas de calendário. Além disso, a classe Appointment permite exportar arquivos de calendário para o formato MSG, facilitando a troca e sincronização de dados em diversas plataformas.

## Aspose.Email.Clients.DeliveryService.Mailgun: Implementa o cliente para o serviço de entrega de emails Mailgun

O namespace [Aspose.Email.Clients.DeliveryService.Mailgun](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/) fornece uma implementação de cliente adaptada para o serviço de entrega de emails Mailgun, facilitando a integração para desenvolvedores que buscam capacidades confiáveis e eficientes de envio de emails. No centro deste namespace está a classe crucial, [MailgunClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/mailgunclient/#mailgunclient-class), que serve como o componente principal para interfacear com a API do Mailgun.

## Aspose.Email.Clients.DeliveryService.SendGrid: Implementa o cliente para o serviço de entrega de emails SendGrid

Dentro do namespace [Aspose.Email.Clients.DeliveryService.SendGrid](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/) encontra-se uma implementação adaptada especificamente para o serviço de entrega de emails SendGrid, oferecendo aos desenvolvedores integração perfeita para envio eficiente de emails. No núcleo deste namespace está a classe-chave, [SendGridClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/#sendgridclient-class), que serve como o componente principal para interfacear com a API do SendGrid.

## Aspose.Email.Clients.Exchange.Dav: Fornece classes para acessar o Exchange Server usando o Protocolo WebDav Exchange Store

O namespace [Aspose.Email.Clients.Exchange.Dav](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/) possui ferramentas para interação com o Exchange Server através do Protocolo WebDav Exchange Store. A classe [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) serve para acessar recursos do Exchange Server.

## Aspose.Email.Clients.Exchange.WebService: Fornece acesso ao MS Exchange Server usando os Serviços Web Exchange (EWS)

[Aspose.Email.Clients.Exchange.WebService](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/) é projetado para fornecer acesso ao Microsoft Exchange Server usando os Serviços Web Exchange (EWS). Sua classe principal, [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), facilita interações com o Exchange Server. O EWSClient permite que os desenvolvedores se conectem ao servidor de forma eficiente e realizem várias operações, incluindo gerenciamento de emails, calendários, contatos, tarefas e pastas públicas. Esta classe suporta funcionalidades como enviar e receber emails, organizar pastas de correio, agendar compromissos e lidar com solicitações de reunião.

## Aspose.Email.Clients.Google: Fornece classes para acessar contas do Google

[Aspose.Email.Clients.Google](https://reference.aspose.com/email/net/aspose.email.clients.google/) é um namespace que fornece classes para acessar e gerenciar contas do Google com facilidade. A classe central dentro deste namespace é a [GmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/gmailclient/). Esta classe permite que os desenvolvedores integrem e interajam com os serviços do Google Mail, aproveitando a autenticação OAuth 2.0.

## Aspose.Email.Clients.Graph: Fornece classes para acessar serviços do Microsoft 365 usando REST API

O [Aspose.Email.Clients.Graph](https://reference.aspose.com/email/net/aspose.email.clients.graph/) é projetado para acessar e gerenciar serviços do Microsoft 365 através da REST API, oferecendo uma abordagem para integrar funcionalidades de email dentro de aplicações .NET. No coração deste namespace está a classe [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/), que permite que os desenvolvedores interajam de forma fluida com os serviços do Microsoft 365. O GraphClient possibilita uma ampla gama de operações, incluindo enviar e receber emails, gerenciar eventos de calendário e lidar com contatos. Com suporte à autenticação OAuth 2.0, garante acesso seguro aos dados do usuário, mantendo conformidade com padrões modernos de segurança. Além disso, o GraphClient facilita a manipulação de pastas, sincronização de caixas de correio e recuperação de metadados de email.

## Aspose.Email.Clients.Imap: Fornece classes para acessar e manipular mensagens usando IMAP

O namespace [Aspose.Email.Clients.Imap](https://reference.aspose.com/email/net/aspose.email.clients.imap/) é projetado para interagir com servidores de email usando o Protocolo de Acesso a Mensagens da Internet (IMAP). Central para este namespace está a classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/), que serve como a interface principal para realizar uma ampla gama de operações de email. Uma vez conectados, os desenvolvedores podem usar o ImapClient para listar, buscar, deletar e pesquisar emails dentro de várias pastas de correio. Além disso, oferece capacidades para gerenciar e manipular essas pastas, incluindo criação, renomeação e exclusão.

## Aspose.Email.Clients.Pop3: Fornece classes para acessar e manipular mensagens usando POP3

O namespace [Aspose.Email.Clients.Pop3](https://reference.aspose.com/email/net/aspose.email.clients.pop3/) foi projetado para agilizar a interação com servidores de email utilizando o Protocolo de Correio da Post Office versão 3 (POP3), oferecendo um conjunto de classes para acessar e manipular mensagens de email. No coração deste namespace está a classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). A classe Pop3Client facilita o estabelecimento de conexões seguras com servidores POP3, suportando uma variedade de mecanismos de autenticação para garantir acesso seguro e confiável. Uma vez conectado, o Pop3Client permite que os desenvolvedores realizem operações essenciais de email, como recuperar mensagens do servidor, listar emails, marcar mensagens específicas para exclusão e buscar detalhes completos da mensagem, incluindo cabeçalhos e anexos. Além disso, fornece suporte embutido para protocolos SSL e TLS.

## Aspose.Email.Clients.Smtp: Fornece classes para enviar mensagens usando SMTP

O namespace [Aspose.Email.Clients.Smtp](https://reference.aspose.com/email/net/aspose.email.clients.smtp/) é projetado para desenvolvedores que buscam integrar a funcionalidade SMTP (Protocolo Simples de Transferência de Mensagens) em suas aplicações .NET para enviar mensagens de email. No núcleo deste namespace está a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/). A classe SmtpClient oferece um conjunto de capacidades, capacitando os desenvolvedores a estabelecer conexões seguras com servidores SMTP e enviar emails. Ela suporta vários métodos de autenticação, garantindo compatibilidade com uma ampla gama de servidores SMTP, e fornece opções para especificar prioridade de mensagem, notificações de entrega e cabeçalhos personalizados. Com suporte embutido para protocolos de criptografia SSL e TLS, a classe SmtpClient garante comunicação segura.

## Aspose.Email.DKIM: Contém classes para trabalhar com assinaturas DKIM

O namespace [Aspose.Email.DKIM](https://reference.aspose.com/email/net/aspose.email.dkim/) oferece classes para lidar com assinaturas de DomainKeys Identified Mail (DKIM), para garantir a integridade e autenticidade dos emails. A classe [DKIMSignatureInfo](https://reference.aspose.com/email/net/aspose.email.dkim/dkimsignatureinfo/) serve como o componente principal para fornecer informações relacionadas ao DKIM.

## Aspose.Email.Mapi: Contém classes que representam mensagens, contatos e compromissos do Outlook e trabalham com o formato de arquivo PST/OST do Microsoft Outlook

O namespace [Aspose.Email.Mapi](https://reference.aspose.com/email/net/aspose.email.mapi/) é projetado para trabalhar com dados do Microsoft Outlook. A classe principal dentro deste namespace é [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), que serve para lidar com mensagens do Outlook. A MapiMessage fornece capacidades para criar, ler, modificar e salvar mensagens do Outlook no formato MSG. Os desenvolvedores podem usar esta classe para acessar e manipular o conteúdo dos itens do Outlook, incluindo o assunto, corpo, anexos, destinatários e propriedades.

Além de gerenciar emails individuais, o namespace Aspose.Email.Mapi também inclui:

- classes para lidar com contatos ([MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/)),
- compromissos ([MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/)),
- e outros itens do Outlook, tornando possível interagir programaticamente com vários elementos normalmente contidos em arquivos PST (Tabela de Armazenamento Pessoal) e OST (Tabela de Armazenamento Offline). Este conjunto de classes permite a integração com formatos de armazenamento de dados do Outlook, facilitando tarefas como migração de emails, backup e sincronização.

## Aspose.Email.PersonalInfo.VCard: Contém classes para trabalhar com o formato de arquivo VCard

O namespace [Aspose.Email.PersonalInfo.VCard](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/) é essencial para desenvolvedores que desejam manipular os formatos de arquivo VCard dentro de suas aplicações. A classe principal dentro deste namespace é a [VCardContact](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/). Esta classe é fundamental para criar, analisar e gerenciar arquivos VCard, que são amplamente utilizados para trocar informações de contato. Com a VCardContact, os desenvolvedores podem ler arquivos VCard para extrair detalhes de contato ou gerar arquivos VCard a partir de dados existentes. Esta classe suporta várias versões de VCard para compatibilidade e flexibilidade no manuseio de diferentes formatos de VCard. Além disso, inclui capacidades para codificação e decodificação de informações de contato, permitindo integração com outros sistemas e plataformas que utilizam padrões VCard.

## Aspose.Email.Printing: Contém classes que representam a funcionalidade de impressão de mensagens

O namespace [Aspose.Email.Printing](https://reference.aspose.com/email/net/aspose.email.printing/) é projetado para fornecer as ferramentas necessárias para imprimir mensagens de email diretamente a partir de aplicações. Um impressor para mensagens de email é representado pela classe [MailPrinter](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/). Esta classe oferece um conjunto de funcionalidades para facilitar a impressão de vários formatos de mensagem, incluindo MSG, EML e MHTML. O MailPrinter torna possível personalizar o layout de impressão, ajustando as configurações de página para garantir que os emails renderizados atendam a requisitos específicos.

## Aspose.Email.Storage.Mbox: Fornece classes para trabalhar com o formato MBOX

O namespace [Aspose.Email.Storage.Mbox](https://reference.aspose.com/email/net/aspose.email.storage.mbox/) oferece um conjunto de classes projetadas para gerenciar e manipular formatos de arquivo MBOX, que são amplamente utilizados para armazenar coleções de mensagens de email. As classes centrais deste namespace são a classe [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/) e a classe [MboxStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragewriter/), que servem como os principais componentes para interagir com arquivos MBOX. 
A classe MboxrdStorageReader fornece capacidades para ler e percorrer arquivos MBOX. Ela permite que os desenvolvedores extraiam mensagens de email individuais, dando a eles a capacidade de processar ou analisar o conteúdo do email de forma programática. Além disso, esta classe suporta a conversão perfeita de mensagens extraídas para outros formatos populares de email, como EML ou MSG, expandindo sua utilidade em diversos cenários de aplicação. 
A classe MboxrdStorageWriter é projetada para criar e escrever arquivos MBOX.

## Aspose.Email.Storage.Olm: Fornece classes para trabalhar com o formato de arquivo Microsoft Outlook OLM

O namespace [Aspose.Email.Storage.Olm](https://reference.aspose.com/email/net/aspose.email.storage.olm/) é um conjunto de classes projetadas para gerenciar e manipular o formato de arquivo OLM do Microsoft Outlook, que é utilizado principalmente para armazenar dados de email no MacOS. Aqui, a classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) é o componente principal responsável por interagir com arquivos OLM. A classe OlmStorage capacita os desenvolvedores com a capacidade de carregar arquivos OLM e, em seguida, extrair, ler e manipular seu conteúdo, incluindo emails, contatos, itens de calendário e anotações. Em particular, permite explorar hierarquias de pastas, filtrar tipos específicos de mensagens e extração eficiente de dados.

## Aspose.Email.Storage.Pst: Fornece classes para trabalhar com o formato de arquivo Microsoft Outlook PST/OST

O namespace [Aspose.Email.Storage.Pst](https://reference.aspose.com/email/net/aspose.email.storage.pst/) oferece classes projetadas para lidar com os formatos de arquivo PST e OST do Microsoft Outlook, que são essenciais para gerenciar dados de email no Windows. Central para este namespace está a classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/), o componente principal responsável por interagir com arquivos PST e OST. A classe PersonalStorage fornece recursos para carregar, criar e manipular esses tipos de arquivo. Ela permite que os desenvolvedores realizem uma ampla gama de operações, incluindo extração e gerenciamento de emails, contatos, entradas de calendário, tarefas e anotações. A classe também suporta navegação hierárquica de pastas, permitindo organização e recuperação de dados eficientes. Além disso, a classe PersonalStorage facilita a conversão de conteúdos de PST e OST para vários outros formatos, como EML, MSG ou MBOX, ampliando sua utilidade.

## Aspose.Email.Storage.Zimbra: Fornece classes para trabalhar com armazenamento Zimbra

[Aspose.Email.Storage.Zimbra](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/) é um namespace dentro da biblioteca Aspose.Email com a classe [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) que serve para acessar e gerenciar arquivos Zimbra TGZ (Tar GZip). A classe TgzReader oferece capacidades para trabalhar com arquivos de email, incluindo a capacidade de analisar e extrair emails, contatos e itens de calendário de arquivos TGZ, especialmente, lendo arquivos TGZ, iterando através de seus conteúdos e acessando programaticamente itens individuais para processamento personalizado.

## Aspose.Email.Tools.Logging: Fornece classes para funcionalidade de registro

O namespace [Aspose.Email.Tools.Logging](https://reference.aspose.com/email/net/aspose.email.tools.logging/) é um namespace para incorporar funcionalidades de registro dentro de aplicações baseadas em email. A classe principal dentro deste namespace é a classe [LoggerManager](https://reference.aspose.com/email/net/aspose.email.tools.logging/loggermanager/#loggermanager-class), que é projetada para oferecer capacidades de registro, permitindo que as aplicações rastreiem e gravem diversos eventos operacionais.

## Aspose.Email.Tools.Merging: Contém classes para construir mensagens de email usando templates

O [Aspose.Email.Tools.Merging](https://reference.aspose.com/email/net/aspose.email.tools.merging/) é um namespace para automatizar a criação de mensagens de email personalizadas através de templates. No coração deste namespace está a classe [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/), que é a classe principal responsável por construir mensagens de email usando templates. A classe TemplateEngine permite a fusão de dados em templates predefinidos, possibilitando a substituição de espaços reservados por informações reais. Isso é particularmente útil para gerar emails personalizados em massa, garantindo que cada destinatário receba uma mensagem única adaptada ao seu contexto específico.

## Aspose.Email.Tools.Search: Contém classes base para busca de mensagens por critérios

O [Aspose.Email.Tools.Search](https://reference.aspose.com/email/net/aspose.email.tools.search/) namespace é projetado para simplificar o processo de localização de mensagens de email com base em uma ampla gama de critérios. O pilar deste namespace é a classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/), que serve como o componente principal responsável por definir parâmetros de busca e executar consultas contra repositórios de email. Com o MailQuery, você pode especificar várias condições de busca, como remetente, destinatário, palavras-chave do assunto, intervalos de data e até termos específicos de conteúdo. Essa capacidade permite filtrar e recuperar mensagens de email relevantes de extensos arquivos ou caixas de entrada atuais. MailQuery suporta a construção de consultas complexas usando operadores lógicos.

## Aspose.Email.Tools.Verifications: Fornece classes para funcionalidade de validação de mensagens

O [Aspose.Email.Tools.Verifications](https://reference.aspose.com/email/net/aspose.email.tools.verifications/) namespace oferece classes que são essenciais para garantir a integridade e validade das mensagens de email. No coração deste namespace está a classe [EmailValidator](https://reference.aspose.com/email/net/aspose.email.tools.verifications/emailvalidator/#emailvalidator-class), que serve como o componente principal para implementar várias verificações de validação em emails.

## Aspose.Email.Windows.Forms: Contém classes para lidar com arquivos arrastados do Outlook em aplicações Windows Forms

[Aspose.Email.Windows.Forms](https://reference.aspose.com/email/net/aspose.email.windows.forms/) é um namespace especializado projetado para facilitar a integração de funcionalidades relacionadas a email dentro de aplicações Windows Forms, particularmente focando no manuseio de arquivos arrastados do Microsoft Outlook. A classe principal neste namespace, [FileDropTargetManager](FileDropTargetManager), fornece aos desenvolvedores capacidades para gerenciar e processar operações de arrastar e soltar envolvendo itens do Outlook. O FileDropTargetManager permite que as aplicações capturem, manipulem e processem mensagens de email, anexos e outros elementos do Outlook quando são arrastados para uma aplicação Windows Forms. Com esta classe, você pode implementar recursos como extrair e exibir o conteúdo dos itens arrastados, salvar anexos em locais específicos ou acionar ações personalizadas com base no tipo de item solto.

## Aspose.Email.Windows.WPF: Contém classes para lidar com arquivos arrastados do Outlook em aplicações Windows Presentation Foundation (WPF)

O [Aspose.Email.Windows.WPF](https://reference.aspose.com/email/net/aspose.email.windows.wpf/) namespace é projetado para permitir a integração de funcionalidades relacionadas a email dentro de aplicações WPF, particularmente focando no manuseio de arquivos arrastados do Microsoft Outlook. O pilar deste namespace é a classe [FileDropPanel](https://reference.aspose.com/email/net/aspose.email.windows.wpf/filedroppanel/), que permite que os desenvolvedores implementem operações de arrastar e soltar. O FileDropPanel atua como um painel especializado que captura itens arrastados do Outlook, incluindo emails, anexos e outros elementos relacionados. Ele detecta automaticamente quando itens são soltos no painel e fornece eventos e métodos para processar esses itens de acordo. Ao utilizar o FileDropPanel, os desenvolvedores podem extrair o conteúdo do email, salvar anexos em locais especificados ou executar lógica de negócios personalizada com base no tipo de item recebido.