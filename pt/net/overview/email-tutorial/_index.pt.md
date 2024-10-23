---
title: "Tutorial de Email"
url: /pt/net/tutorial-email/
weight: 5
type: docs
---

## **Formatos de Arquivo de Email Mais Populares**

### MSG 

**Microsoft Outlook Message (MSG)** é um formato de email proprietário usado pelo Microsoft Outlook para armazenar mensagens de email individuais. Esses arquivos contêm o conteúdo do email e metadados, como remetente, destinatários, assunto e horários. Eles suportam formatação rica, anexos e recursos específicos do Outlook, como bandeiras, importância e sensibilidade.

#### Recursos principais

- O arquivo MSG representa uma única mensagem de email.
- Arquivos MSG estão associados ao Microsoft Outlook e podem ser abertos por ele.
- Arquivos MSG são comumente usados para arquivamento, backup e troca de itens do Outlook entre diferentes instâncias do Outlook ou outros clientes de email compatíveis.

MSG está intimamente relacionado no contexto do Microsoft Outlook e da **Messaging Application Programming Interface (MAPI)**. MAPI é uma interface de programação que permite que aplicativos interajam com serviços de mensagens, principalmente Microsoft Exchange Server e Microsoft Outlook. Ele fornece um conjunto de funções e protocolos para enviar, receber e gerenciar mensagens de email, assim como acessar outros recursos relacionados a mensagens, como calendários, contatos e tarefas. MAPI é usado pelo Microsoft Outlook para criar, manipular e gerenciar mensagens de email. Quando um usuário compõe ou recebe um email no Outlook, o MAPI gerencia a comunicação subjacente com o servidor de email e fornece as funções necessárias para gerenciar o conteúdo da mensagem.

#### Base Técnica para o Formato MSG

Os arquivos MSG armazenam dados de mensagem usando **propriedades MAPI**, que são atributos que definem vários aspectos da mensagem. Essas propriedades incluem atributos padrão, como remetente, destinatário, assunto e horários, bem como propriedades personalizadas e atributos estendidos. As propriedades organizam a mensagem em uma estrutura hierárquica, com propriedades de nível superior definindo os atributos gerais da mensagem e propriedades aninhadas representando componentes específicos, como destinatários, anexos e objetos incorporados. Os arquivos MSG podem conter várias streams de propriedade, cada uma contendo um conjunto de propriedades MAPI relacionadas. Essas streams são estruturadas de acordo com o **Compound File Binary Format (CFBF)** e armazenam tanto propriedades padrão quanto personalizadas.

### OFT

**Outlook File Template (OFT)** são formatos de email usados pelo Microsoft Outlook para criar mensagens padronizadas. Ao contrário dos arquivos MSG, os arquivos OFT não contêm o conteúdo real da mensagem, mas servem como templates com formatação, layout e marcadores de posição pré-definidos para conteúdo dinâmico. 

#### Recursos principais

 - Os arquivos OFT agilizam a criação de emails repetitivos ao fornecer templates pré-desenhados para cenários comuns, como newsletters, anúncios ou respostas.
 - Ao usar templates OFT, as organizações garantem consistência em branding, formatação e mensagens em todas as comunicações externas.
 - Os usuários podem personalizar templates OFT adicionando ou modificando conteúdo antes de enviar, permitindo mensagens personalizadas enquanto mantêm uma formatação padronizada.

### EML

**EML** é um dos formatos de arquivo de email mais amplamente reconhecidos e utilizados, projetado principalmente para aderir ao padrão **MIME (Multipurpose Internet Mail Extensions)**. Esse formato é amplamente suportado em vários clientes e sistemas de email devido à sua abordagem aberta e generalizada para armazenamento e transmissão de emails.

#### Recursos Principais

- Cada arquivo EML encapsula uma única mensagem de email juntamente com seus metadados associados, como remetente, destinatários, assunto e horários.
- Os arquivos EML suportam formatação rica, anexos e elementos incorporados, aderindo ao padrão MIME, que permite uma representação versátil do conteúdo do email.
-  Ao contrário de formatos proprietários, como MSG (Microsoft Outlook Message), que estão intimamente ligados a softwares específicos (Outlook e MAPI), os arquivos EML oferecem uma abordagem mais universal compatível com vários programas de email em diferentes plataformas. Os arquivos EML são compatíveis com uma infinidade de clientes de email, incluindo, mas não se limitando a, Microsoft Outlook, Mozilla Thunderbird, Apple Mail e muitos serviços de email baseados na web.

#### Base Técnica para o Formato EML

O formato de arquivo EML está intrinsecamente ligado ao padrão MIME, que é uma especificação para o formato dos corpos das mensagens da Internet. O MIME estende o formato de email básico para suportar texto em conjuntos de caracteres diferentes do ASCII, bem como anexos de conteúdo multimídia.

**Estrutura MIME:**

   - Um arquivo EML começa com a seção de cabeçalho, contendo informações como De, Para, Assunto, Data e outros cabeçalhos. Cabeçalhos adicionais podem incluir Content-Type, Content-Transfer-Encoding e mais.
   - Após os cabeçalhos, o corpo de um arquivo EML é apresentado. Esta seção pode conter texto simples, HTML ou conteúdo multipart, permitindo a combinação de diferentes tipos de conteúdo em uma única mensagem.
   - Um arquivo EML pode incluir anexos codificados em base64, permitindo que dados binários sejam transferidos via email. Esses anexos são definidos dentro de suas próprias partes MIME com cabeçalhos apropriados indicativos do tipo de arquivo e codificação.

**Tipos MIME:**

O conteúdo de um arquivo EML é dividido em vários tipos MIME para diferenciar texto, HTML e outros tipos de mídia. Tipos MIME comuns encontrados em um arquivo EML incluem:

- `text/plain` para mensagens de texto simples.
- `text/html` para mensagens formatadas em HTML.
- `multipart/mixed` para emails que incluem tanto o conteúdo da mensagem quanto anexos.
- `application/octet-stream` para anexos de arquivos binários.

### TNEF

**Transport Neutral Encapsulation Format (TNEF)** é um formato de email proprietário usado pelo Microsoft Outlook e Microsoft Exchange Server para encapsular propriedades de email e conteúdo de texto rico que pode não ser suportado por protocolos de email padrão. 
É usado principalmente por clientes de email da Microsoft para codificar e transmitir formatação de texto rica, objetos incorporados e outros recursos de email proprietários, garantindo que conteúdo complexo de email, como formatação, arquivos incorporados e eventos de calendário, sejam preservados quando emails são enviados entre diferentes clientes de email da Microsoft.

#### Recursos Principais

- O TNEF pode encapsular uma ampla variedade de propriedades MAPI, formatação de texto rico específica da Microsoft e propriedades especiais que não podem ser transmitidas através de emails padrão MIME ou de texto simples.
- Itens do Outlook, como Calendário, Contatos, Tarefas e Notas podem ser encapsulados dentro do formato TNEF.
- Clientes de email que não são da Microsoft podem não entender ou processar corretamente anexos TNEF, muitas vezes resultando no irritante arquivo `winmail.dat`. Isso geralmente acontece porque eles não conseguem decodificar a formatação proprietária codificada no TNEF.

#### Base Técnica para o Formato TNEF

- O TNEF encapsula o conteúdo do email em um arquivo de anexo binário especial. Esse anexo normalmente possui a extensão `.dat`, mais comumente chamado de `winmail.dat`.
- Os dados TNEF estão frequentemente associados ao tipo MIME `application/ms-tnef`.
- O formato TNEF representa uma hierarquia de propriedades de mensagens como uma estrutura plana, que pode ser vista como um fluxo de dados sequencial. O formato típico de uma propriedade específica no fluxo inclui um identificador com informações sobre o tipo de dado, tamanho (se não definido pelo tipo), e dados.

## **Formatos Comuns de Armazenamento de Email**

### MBOX

**MBOX (abreviação de Mailbox)** é um formato de armazenamento de emails amplamente utilizado que está presente há várias décadas. Ele é usado para armazenar uma coleção de mensagens de email em um único arquivo, com cada mensagem concatenada e demarcada por uma linha separadora. 

O MBOX foi desenvolvido pela primeira vez na década de 1970 e desde então viu várias versões e implementações ao longo dos anos. Ele foi implementado em numerosos clientes de email, como Unix mail, Mozilla Thunderbird, Eudora e mais.

#### Recursos Principais

- O MBOX é suportado em uma ampla gama de plataformas, incluindo Unix, Linux e macOS.
- Clientes como Mozilla Thunderbird, Apple Mail e muitos outros podem ler e escrever arquivos MBOX.
- A natureza de texto simples do formato torna simples a análise e o processamento usando ferramentas de manipulação de texto.
- Devido à sua estrutura simples, o MBOX é amplamente usado para arquivamento e finalidades de backup.
- Como todos os emails são armazenados em um único arquivo, o arquivo pode se tornar bastante grande ao longo do tempo, levando a ineficiências.
#### Variedades do MBOX

O MBOX vem em várias variantes, cada uma com pequenas diferenças em como eles lidam com mensagens:

- **MBOXO:** O formato original onde as linhas "From " no corpo do email são citadas com um caractere >.
- **MBOXRD:** Uma variante do MBOXO que estende ainda mais o método de citação das linhas "From ".
- **MBOXCL:** Introduzido pela variante "Clássica" do MBOX, onde cada linha "From " é citada com uma string ffrom.
- **MBOXCL2:** Uma variação do MBOXCL onde as linhas "From " são duplicadas para distingui-las.

#### Base Técnica para o Formato MBOX

**Estrutura do Arquivo:**
  - Um arquivo MBOX é um arquivo de texto simples que contém uma série de mensagens EML.
  - Cada mensagem começa com uma linha "From " (um espaço após a palavra "From") que geralmente inclui o endereço de email do remetente e o timestamp quando a mensagem foi recebida.
  - Cada mensagem é seguida por uma linha em branco para separá-la da próxima mensagem.
  
    **Exemplo:**
    
    ```
    From user@example.com Fri Jan 01 00:00:00 2021
    (Cabeçalhos)
    
    (Corpo)
    
    From user2@example.com Fri Jan 01 00:01:00 2021
    (Cabeçalhos)
    
    (Corpo)
    ```

### PST/OST

 **Personal Storage Table (PST)** e **Offline Storage Table (OST)** são formatos de arquivo usados pelo Microsoft Outlook para armazenar cópias de emails, eventos de calendário e outros itens.
 
#### Recursos Principais

- Arquivos PST são usados para armazenar informações pessoais e são normalmente usados para arquivar emails e dados mais antigos. Utilizados principalmente por usuários domésticos e pequenas organizações para armazenamento local de mensagens de email, contatos e eventos de calendário.
- Arquivos OST são usados para armazenamento offline e sincronização de emails e outros dados com o servidor Exchange. Usados principalmente por usuários que acessam o Microsoft Exchange Server ou Office 365.
- Armazenados localmente no computador de um usuário. Podem ser acessados mesmo quando o usuário não está conectado ao servidor de email.
- Arquivos PST podem ser facilmente feitos backup e transferidos para outros computadores. Os usuários podem transferir arquivos PST entre diferentes sistemas ou versões do Outlook.
- Arquivos OST não são destinados a backup ou transferência manual, pois são cópias sincronizadas de dados do servidor. Arquivos OST estão vinculados a perfis específicos e não podem ser movidos facilmente para diferentes sistemas.

### OLM

 **Outlook for Mac Archive File (OLM)** é um formato de arquivo usado pelo Microsoft Outlook para Mac para armazenar mensagens de email, eventos de calendário, contatos, tarefas e outros itens.
 
#### Recursos Principais

- Arquivos OLM são principalmente usados para arquivar e fazer backup de emails e outros itens do Outlook em sistemas Mac.
- Arquivos OLM são armazenados localmente no Mac do usuário.
- Arquivos OLM podem ser abertos e acessados via Microsoft Outlook para Mac. Eles não são diretamente compatíveis com o Outlook para Windows sem conversão.
- Não há um limite de tamanho fixo para arquivos OLM imposto pela Microsoft, mas problemas de desempenho podem ocorrer se o arquivo se tornar muito grande. Os usuários normalmente gerenciam o tamanho criando vários arquivos menores em vez de um grande arquivo OLM.
- Backup: Como os arquivos OLM são armazenados localmente, podem ser feitos backup ou copiados para dispositivos de armazenamento externos.

### TGZ

**TGZ**  (usado pelo Zimbra para arquivo de backup de caixa de correio) é um formato de arquivo usado para arquivamento e compressão de dados, comumente associado a sistemas Unix e Linux. O termo "TGZ" refere-se a uma combinação de duas utilidades: "tar" (Tape Archive) e "gzip." O formato de arquivo .tar agrupa vários arquivos e diretórios em um único arquivo de archive. Ele preserva informações do sistema de arquivos, como estruturas de diretório, permissões de arquivos e horários. O formato de arquivo .gz comprime dados, tornando o arquivo tar menor e mais fácil de gerenciar ou transferir. A natureza compactada do TGZ torna-o adequado para transferir arquivos de email pela internet ou movê-los entre sistemas.

### NSF

 **Notes Storage Facility (NSF)** é um formato de arquivo proprietário usado principalmente pelo IBM Lotus Notes (agora HCL Notes) para armazenar diversos tipos de dados, incluindo email, eventos de calendário, tarefas e outros dados de aplicativos. Os arquivos NSF usam um modelo de banco de dados NoSQL, baseado em documentos. Cada banco de dados é armazenado como um único arquivo NSF com extensão .nsf. A extensão representa um formato de banco de dados usado pelo IBM Notes e Domino Server. Cada email, entrada de calendário ou tarefa é armazenado como um documento que pode conter vários tipos de dados, como texto, anexos, links, formatação de texto rico e até mesmo metadados.
 
## **Protocolos de Email**

### SMTP

**SMTP (Simple Mail Transfer Protocol)** é um protocolo usado para enviar e receber mensagens de email pela Internet. É uma parte crucial do processo de comunicação por email e é principalmente responsável por transferir emails do servidor de email do remetente para o servidor de email do destinatário, bem como submeter emails de um cliente para um servidor. A porta padrão para SMTP é 25 para comunicação entre servidores de email. A porta 587 e a porta 465 também são usadas para SMTP, sendo a 587 frequentemente usada para envio de email e a 465 para SMTP sobre SSL (SMTPS). O SMTP é definido pela [versão RFC 5321](https://datatracker.ietf.org/doc/html/rfc5321).

#### Recursos Principais

- Suporta mecanismos de autenticação (por exemplo, SMTP AUTH) para garantir que apenas usuários autorizados possam enviar emails pelo servidor.
- O SMTP pode usar SSL/TLS para criptografar a conexão entre o cliente e o servidor, garantindo que os dados do email sejam transmitidos com segurança.
- Fornece mensagens de erro detalhadas e códigos de status para indicar o sucesso ou a falha da transmissão de email.
- O SMTP pode gerenciar mensagens multipart, permitindo a inclusão de anexos e diversos tipos de conteúdo em um email.
- O SMTP é um protocolo amplamente aceito e padronizado, garantindo compatibilidade entre diferentes sistemas e clientes de email (por exemplo, Microsoft Outlook, Mozilla Thunderbird usam SMTP para enviar emails saindo). Sistemas e aplicações automatizados usam SMTP para enviar notificações, alertas e outros emails automatizados.

### IMAP

**Internet Message Access Protocol (IMAP)** é um protocolo padrão usado por clientes de email para acessar, recuperar e gerenciar mensagens de email de um servidor de email. Entre os clientes suportados estão Microsoft Outlook, Mozilla Thunderbird, Apple Mail e muitos serviços de webmail, como Gmail, Yahoo Mail e Outlook.com. A versão mais comumente usada é o IMAP4, definida pela [RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501). Ao contrário do **POP (Post Office Protocol)**, que baixa emails para um dispositivo local, o IMAP armazena emails no servidor. A capacidade de visualizar e gerenciar mensagens de email diretamente no servidor de email oferece flexibilidade para acessá-las de múltiplos dispositivos e locais, reduzindo o risco de perda de dados se um dispositivo for perdido ou danificado. O IMAP sincroniza o cliente de email com o servidor, garantindo que as alterações feitas em um cliente (como ler ou excluir um email) sejam refletidas em todos os outros clientes. O IMAP geralmente usa a porta 143 para comunicações não criptografadas e a porta 993 para comunicações criptografadas (SSL/TLS).

#### Recursos Principais

- Gerenciamento de Pastas. O IMAP permite que os usuários criem, excluam e renomeiem pastas no servidor de email. Suporta estruturas de pastas hierárquicas para organizar emails.
- O IMAP acompanha o status de cada email (por exemplo, lido, não lido, sinalizado, respondido). Essas bandeiras de status são armazenadas no servidor, portanto, são consistentes em todos os dispositivos.
- O IMAP pode buscar partes específicas de um email, como cabeçalhos ou partes do corpo, o que pode ser útil para visualizar emails ou manusear anexos grandes.
- O IMAP suporta pesquisa e filtragem do lado do servidor de emails com base em vários critérios, permitindo que os clientes recuperem mensagens específicas sem baixar todos os emails.
- Vários clientes podem acessar a mesma caixa de correio simultaneamente. O IMAP gerencia o acesso concorrente e atualiza o estado dos emails em tempo real.
- Dependência do Servidor. Como os emails são armazenados no servidor, uma conexão de internet confiável é necessária para acessar e gerenciar emails. O tempo de inatividade do servidor pode impactar a disponibilidade dos emails.
- O IMAP pode usar SSL/TLS para criptografar a conexão entre o cliente e o servidor, garantindo que os dados do email sejam transmitidos de forma segura.
- O IMAP suporta vários métodos de autenticação, incluindo OAuth, para verificar as identidades dos usuários de forma segura.

#### Extensões de Protocolo

- **IMAP IDLE:** Uma extensão que permite ao servidor notificar o cliente sobre novas mensagens ou alterações em tempo real, reduzindo a necessidade de polling frequente.
- **IMAP QUOTA:** Uma extensão que fornece mecanismos para gerenciar e relatar limites de armazenamento, ajudando os usuários a gerenciar o tamanho da caixa de correio.
- **IMAP MOVE:** Uma extensão que otimiza o processo de mover mensagens entre pastas no servidor, melhorando o desempenho.

### POP3

 **Post Office Protocol versão 3 (POP3)** é um protocolo usado por clientes de email, como Microsoft Outlook, Mozilla Thunderbird e Apple Mail, para recuperar email de um servidor de email. É um dos protocolos mais antigos e simples para recuperação de email, projetado para baixar emails para um dispositivo local e, opcionalmente, excluí-los do servidor.

#### Recursos Principais

- Como os emails são baixados para o dispositivo local, os usuários podem acessar seus emails offline sem precisar de uma conexão constante à internet.
- O POP3 é simples de configurar e usar, tornando-se acessível para usuários que precisam de recuperação de email básica sem recursos avançados.
- O POP3 não sincroniza emails entre vários dispositivos. Uma vez que um email é baixado para um dispositivo, ele não está mais disponível no servidor por padrão.
- O POP3 fornece capacidades limitadas de gerenciamento do lado do servidor. Recursos avançados, como gerenciamento de pastas, pesquisa do lado do servidor e bandeiras de status de mensagens não são suportados.
- Como os emails são armazenados localmente, os usuários precisam garantir que façam backup de seus dados de email para prevenir perda em caso de falha do dispositivo.
- Os usuários podem configurar as configurações do POP3 para excluir emails do servidor imediatamente após o download, após um período especificado ou quando excluídos do cliente local.
- O POP3 pode usar SSL/TLS para criptografar a conexão entre o cliente e o servidor, garantindo que os dados do email sejam transmitidos com segurança.

#### Versões e Extensões do Protocolo

- **POP3 sobre SSL (POP3S)** é uma versão do POP3 que opera sobre uma conexão SSL/TLS, proporcionando comunicação criptografada entre o cliente e o servidor.
- **APOP (Authenticated Post Office Protocol)** é uma extensão que fornece um método de autenticação mais seguro usando senhas hash.

## **API para Acessar Serviços de Email**

### Exchange Web Dav (foi oficialmente descontinuado)

**Exchange WebDAV (Web Distributed Authoring and Versioning)** era uma extensão de protocolo usada pelo Microsoft Exchange Server para permitir que clientes acessassem e manipulassem itens de email, calendário e contatos armazenados no servidor via HTTP. Embora tenha sido oficialmente descontinuado, desempenhou um papel significativo no desenvolvimento do acesso baseado na web e remoto aos dados do Exchange.

### EWS

**Exchange Web Services (EWS)** é uma API fornecida pela Microsoft para interagir com o Microsoft Exchange Server. Permite que os desenvolvedores acessem e manipulem dados do Exchange, como emails, eventos de calendário, contatos e tarefas programaticamente. O EWS foi introduzido para substituir protocolos mais antigos, como WebDAV, e fornece uma maneira mais robusta e eficiente de trabalhar com dados do Exchange. 

Ele usa o SOAP (Simple Object Access Protocol) sobre HTTP e HTTPS para enviar e receber mensagens entre o cliente e o servidor Exchange. A natureza baseada em SOAP do EWS pode ser complexa de implementar e depurar em comparação com APIs RESTful. A Microsoft está gradualmente migrando para a Microsoft Graph API, que oferece uma abordagem mais moderna e RESTful para acessar dados do Microsoft 365, incluindo Exchange Online.

### Microsoft Graph

**Microsoft Graph** é uma API poderosa que fornece um endpoint unificado para acessar uma ampla gama de dados e serviços no ecossistema Microsoft 365. Permite que os desenvolvedores interajam com uma variedade de serviços da Microsoft, incluindo Office 365, Azure Active Directory, SharePoint, OneDrive, Outlook, Microsoft Teams e mais. Serve como um gateway para dados e insights em todo o Microsoft 365.

#### Recursos Principais

- A URL base para a API é https://graph.microsoft.com.
- Usa OAuth 2.0 para autenticação e autorização.
- Aproveita as capacidades de IA e aprendizado de máquina da Microsoft para obter insights de dados aprimorados.

### Gmail API

**Gmail API** é uma API RESTful fornecida pelo Google que permite que desenvolvedores interajam programaticamente com caixas de entrada do Gmail e realizem várias operações em dados de email (ler, enviar, excluir e organizar mensagens de email). Oferece uma alternativa mais flexível e poderosa aos protocolos tradicionais IMAP e SMTP, permitindo que os desenvolvedores acessem e gerenciem mensagens, threads, labels, rascunhos e mais. Está disponível através da Google Cloud Platform.

#### Recursos Principais

- Realizar várias requisições de API em uma única chamada HTTP para melhorar a eficiência e reduzir o número de requisições de rede.
- Usa OAuth 2.0 para autenticação e autorização seguras, garantindo que as aplicações acessem apenas os dados que os usuários explicitamente autorizaram.
- Fornece vários escopos de permissão, permitindo que as aplicações solicitem apenas o nível de acesso que precisam (por exemplo, acesso somente leitura, acesso completo).
- Todas as interações da API ocorrem através de HTTPS para garantir comunicação segura entre a aplicação e os servidores do Google.

## **Tecnologias Avançadas**

### S/MIME

**Secure/Multipurpose Internet Mail Extensions (S/MIME)** é um padrão amplamente utilizado para proteger a comunicação por email. Ele fornece um método para enviar e receber mensagens de email assinadas e criptografadas, garantindo a integridade, autenticidade e confidencialidade da mensagem.

#### Recursos Principais

- O S/MIME garante que apenas o destinatário pretendido possa ler o conteúdo do email. Usa uma combinação de algoritmos de criptografia simétrica (para velocidade) e assimétrica (para troca de chaves). Algoritmos comumente usados incluem RSA (usado para criptografia assimétrica), AES ou Advanced Encryption Standard (um dos algoritmos simétricos) e Triple DES.
- Confirma a identidade do remetente. 
- Verifica que o conteúdo do email não foi alterado durante o trânsito. Impede que o remetente negue a autoria do email. 
- Usa a chave privada do remetente para criar uma assinatura e o cliente do destinatário usa a chave pública do remetente para verificá-la.
- O S/MIME depende de uma Infraestrutura de Chave Pública (PKI) para gerenciamento e troca de chaves. Certificados digitais, emitidos por Autoridades Certificadoras (CAs), vinculam chaves públicas a identidades individuais. Os certificados geralmente seguem o padrão X.509.

### DKIM

**DomainKeys Identified Mail (DKIM)** é um mecanismo de autenticação de email projetado para detectar endereços de remetente falsificados, uma técnica comum usada em phishing e spoofing de email. Permite que uma organização assuma a responsabilidade por um email durante seu trânsito ao associar um nome de domínio com a mensagem, garantindo assim sua autenticidade e integridade. O DKIM verifica que um email supostamente vindo de um domínio específico foi realmente autorizado pelo proprietário do domínio, focando principalmente na autenticidade do endereço de email "De". Isso é alcançado permitindo que o remetente assine eletronicamente seu email com uma chave privada, enquanto o destinatário verifica essa assinatura usando uma chave pública publicada nos registros DNS do remetente.

#### Recursos Principais

- O DKIM adiciona um cabeçalho "DKIM-Signature" ao email, que contém a assinatura digital e vários parâmetros chave. O corpo do email e cabeçalhos selecionados são hash usando um algoritmo de hash como SHA-256. Esse hash é então criptografado usando a chave privada do remetente para gerar a assinatura digital.
- O remetente publica a chave pública em seus registros DNS. O servidor de email do destinatário consulta a chave pública do remetente no DNS para verificar a assinatura digital.

### AMP Email

**Accelerated Mobile Pages (AMP)** para Email é uma estrutura de código aberto projetada para criar experiências de email dinâmicas, interativas e envolventes. É projetada para tornar os emails mais dinâmicos e funcionais, transformando um meio que é tradicionalmente estático e passivo.

#### Recursos principais

- Permite que os usuários realizem ações diretamente dentro do email, como confirmar presença em eventos, preencher formulários ou interagir com carrosséis de produtos.
- Emails podem servir conteúdo dinâmico que se atualiza no momento da abertura. Isso garante que os usuários vejam as informações mais atuais, seja sobre preços, status de estoque ou atualizações de notícias.
- Emails AMP são suportados por vários dos principais clientes de email, incluindo Gmail, Yahoo Mail e Outlook.com. Cada cliente de email que suporta emails AMP mantém seu próprio conjunto de requisitos e regras de renderização.
- Emails AMP precisam ser enviados em um formato MIME multipart contendo uma versão de texto simples para acessibilidade básica, uma versão HTML para conteúdo rico e visualmente atraente e uma versão AMP para elementos dinâmicos e interativos, garantindo compatibilidade e uma experiência aprimorada do usuário em vários clientes de email.
- Apenas remetentes verificados podem enviar emails AMP, garantindo que os emails sejam seguros e confiáveis.

### AntiSpam

AntiSpam refere-se a uma gama de técnicas, tecnologias e estratégias projetadas para detectar, prevenir e mitigar mensagens de email não solicitadas e frequentemente prejudiciais, comumente conhecidas como spam. 

#### Técnicas AntiSpam

1. **Métodos de Filtragem**
   - Filtragem Baseada em Conteúdo: Analisa o conteúdo do email em busca de indicadores comuns de spam.
   - Listas Negras: Listas de endereços IP ou domínios de spam conhecidos que são automaticamente bloqueados.
   - Listas Brancas: Listas de remetentes aprovados que sempre são permitidos.
   - Filtragem Heurística: Usa regras e algoritmos para detectar spam com base em padrões.
   - Filtragem Bayesiana: Usa métodos estatísticos para identificar spam com base em dados históricos.
   - Greylisting: Rejeita temporariamente emails de remetentes desconhecidos e os aceita se forem enviados novamente após um atraso.
   - Aprendizado de Máquina: Usa modelos complexos treinados em grandes conjuntos de dados para identificar spam.

2. **Métodos de Autenticação**
   - SPF (Sender Policy Framework): Verifica se o endereço IP do remetente está autorizado a enviar emails para o domínio.
   - DKIM (DomainKeys Identified Mail): Usa assinaturas digitais para verificar que o email não foi alterado durante o trânsito e é realmente do domínio que afirma ser.
   - DMARC (Domain-based Message Authentication, Reporting & Conformance): Baseia-se em SPF e DKIM para fornecer um método padronizado para que os remetentes de email indiquem que suas mensagens estão protegidas e como os servidores receptores devem lidar com falhas de autenticação.

### Bounces de Email

#### Tipos de Bounces de Email

1. **Hard Bounces.** Falhas permanentes de entrega indicando que o email não pode ser entregue ao endereço do destinatário.
   - Causas Comuns:
     - Endereços de email inválidos ou inexistentes.
     - O domínio do destinatário não existe.
     - Problemas permanentes no servidor do destinatário.
     - Erros de digitação ou formatação no endereço de email.

2. **Soft Bounces.** Falhas temporárias de entrega indicando que o email não pôde ser entregue no momento, mas pode ser bem-sucedido se tentado novamente depois.
   - Causas Comuns:
     - A caixa de correio do destinatário está cheia.
     - Problemas temporários no servidor do destinatário.
     - O servidor de email do destinatário está offline ou em manutenção.
     - Emails muito grandes para o sistema de email do destinatário.

Os servidores de email normalmente retornam códigos de bounce que podem ajudar a diagnosticar o motivo do bounce.

### Threading de Email

O threading de email é um método usado por clientes e aplicativos de email para agrupar emails relacionados com base em seu assunto ou conversa, facilitando para os usuários acompanhar e gerenciar trocas de email.

#### Recursos principais

- **In-Reply-To e Referências Cabeçalhos**. Cabeçalhos de email que apontam para mensagens anteriores no thread, ajudando o cliente de email a vincular respostas e reenvios ao email original.
- Linhas de Assunto. Muitas vezes usadas para agrupar emails em threads. Emails com a mesma linha de assunto, normalmente precedidos por "Re:" (resposta) ou "Fwd:" (encaminhamento), são agrupados.
- Os usuários podem expandir ou colapsar threads, focando apenas nas partes relevantes de uma conversa.