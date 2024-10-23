---
title: "Novidades no Aspose.Email para .NET"
url: /pt/net/whats-new/
weight: 5
type: docs
---


## [Aspose.Email para .NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Suporte para Contatos e Calendário no MS Graph** - Os métodos da interface IGraphClient permitem acessar, gerenciar e interagir com os contatos e eventos de calendário dos usuários:
  - Recuperar uma coleção de contatos MAPI.
  - Recuperar um contato específico.
  - Criar um novo contato.
  - Atualizar um contato existente.
  - Recuperar uma coleção de informações do calendário.
  - Recuperar uma coleção de itens do calendário.
  - Recuperar um item de calendário específico.
  - Criar um novo item de calendário.
  - Atualizar um item de calendário existente.

## [Aspose.Email para .NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Manipular Categorias de Itens do Outlook** - Aspose.Email torna possível recuperar e utilizar as cores de categoria associadas às categorias de itens do Outlook armazenadas em arquivos OLM.

- **Correspondência de Classe de Contêiner** - uma nova propriedade [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) foi adicionada à classe [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class), que, ao adicionar uma pasta a um arquivo PST, permite garantir que a classe da pasta corresponda ao tipo ou categoria esperado de pastas dentro do arquivo PST.

## [Aspose.Email para .NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Definir Caminho Relativo para Recursos ao Salvar Mensagem de Email como HTML** - Aspose.Email introduz a capacidade de salvar recursos de email com caminhos relativos ao exportar mensagens para o formato HTML, oferecendo maior flexibilidade para o link de recursos. Os usuários podem escolher entre caminhos absolutos e relativos, e definir caminhos personalizados usando o evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event), agilizando o compartilhamento e a exibição de emails em diferentes sistemas.

## [Aspose.Email para .NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Validar Mensagens de Email** - Um conjunto de componentes foi adicionado para permitir que os usuários validem arquivos de mensagem, suportando formatos como eml, emlx, mht, msg e oft. Ao utilizar essa funcionalidade, os usuários podem validar mensagens e obter insights sobre o processo de validação, incluindo tipo de formato e erros encontrados.

- **Anexar Assinaturas Digitais a Mensagens de Email** - O método *AttachSignature* na classe [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) foi projetado para adicionar facilmente uma assinatura digital a um email.

Uma vez que a assinatura esteja anexada, os usuários podem verificar os resultados através de propriedades como 'IsSigned', 'MessageClass' e detalhes do anexo.

Para personalizar o processo de anexação da assinatura, os usuários podem utilizar a classe [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class).

## [Aspose.Email para .NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Dividir Armazenamento Mbox em Partes Menores** - dividir arquivos grandes em partes manejáveis e implementar ações personalizadas durante o processo:

  - Especificar um prefixo personalizado para os nomes dos arquivos Mbox divididos.
  - Personalizar ações antes e depois que um email é copiado para um novo arquivo Mbox.
  - Reagir quando um novo arquivo Mbox é criado.
  - Responder quando um novo arquivo Mbox é preenchido com emails.

- **Obter Conteúdo de AlternateView por MediaType** - recuperar o conteúdo como uma string de um AlternateView específico dentro de uma mensagem de email. O método [MailMessage.GetAlternateViewContent(string mediaType)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) permite acessar o conteúdo de um AlternateView que corresponda ao tipo de mídia especificado.

## [Aspose.Email para .NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Enviar Emails via Graph Client** - adicionado suporte para métodos sobrecarregados à classe GraphClient que aceitam um objeto MailMessage para o envio de emails:
  - [CreateMessage(string folderId, MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Send(MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Salvar Lista de Distribuição Mapi em um Único Arquivo VCF de Múltiplos Contatos** - Salvar a lista de distribuição Mapi em um nome de arquivo especificado usando as opções de salvamento fornecidas. Você pode fornecer o nome do arquivo e uma instância da classe MapiDistributionListSaveOptions como parâmetros.
  - O método void [Save(string fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) foi adicionado para esse fim.

## [Aspose.Email para .NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Excluir Itens do PST** - Adicionamos um novo método, [DeleteItem(string entryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), à classe PersonalStorage. Este método fornece uma maneira de excluir itens (pastas ou mensagens) de uma Tabela de Armazenamento Pessoal (PST) usando o entryId exclusivo associado ao item.
- **Tratamento de Eventos e Divisão de PST** - Funcionalidade Melhorada na classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class):
  - O evento [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) ocorre antes que o armazenamento seja processado, especificamente antes do processamento do armazenamento atual nos métodos MergeWith ou SplitInto. Este evento fornece uma oportunidade para executar lógica personalizada ou lidar com certas operações antes que o processamento do armazenamento ocorra.

  - A classe [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) fornece dados para o evento PersonalStorage.StorageProcessing. 

  - O método sobrecarregado [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) permite a divisão do armazenamento PST em partes menores.
- **Manipulação de Calendário** - Novas propriedades e um método foram adicionados à classe CalendarReader:
  - A propriedade [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) permite recuperar o número de componentes Vevent (eventos) presentes no calendário, facilitando o acompanhamento do número total de eventos.
  - A propriedade [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) determina se o calendário contém vários eventos.
  - A propriedade [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) obtém o tipo de método iCalendar associado ao objeto de calendário. Retorna o tipo de método, como "REQUEST", "PUBLISH" ou "CANCEL", fornecendo informações valiosas sobre o propósito do calendário.
  - A [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) obtém a versão do iCalendar.
  - O método [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) permite o carregamento de uma lista de eventos de um calendário contendo vários eventos. Retorna uma lista de objetos Appointment, permitindo fácil acesso e processamento de cada evento individualmente.

## [Aspose.Email para .NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Preservar ou Remover Assinatura na Conversão MBOX para PST** - defina a propriedade [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) como 'true' para remover a assinatura.
- **Remover Assinatura ao Carregar Arquivos EML** - defina a propriedade [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) como 'true' para remover a assinatura.
- **Verificação de Assinatura de Email**
  - Adicionada uma nova classe [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) para verificar a assinatura de emails seguros. Agora é possível verificar a assinatura de objetos MapiMessage e MailMessage.
  - Adicionada uma nova classe [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) para armazenar os resultados da verificação de emails seguros.

  Métodos introduzidos do SecureEmailManager:

  - [CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) 
  - [CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Aspose.Email para .NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Determinar a Versão dos Arquivos ICS/VCS** - Use a propriedade [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) da classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) para recuperar a versão dos arquivos ICS/VCS.
- **Personalizar Opções de Salvamento para Arquivos VCard** - Adicionamos a nova classe [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) à nossa API com as seguintes propriedades:
  - [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) permite que os usuários especifiquem a versão vCard desejada ao salvar itens de contato. Por padrão, a classe é definida para usar a versão vCard 2.1 (VCardVersion.V21).
  - [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - permite que os usuários controlem se campos estendidos podem ser usados ao salvar arquivos vCard. Quando definido como verdadeiro (padrão), extensões são permitidas, proporcionando compatibilidade com campos personalizados e informações de contato adicionais.
  - [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - a codificação a ser usada ao salvar itens de contato vCard.
- **Obter o Número Total de Itens de Mensagem Contidos na Armazenagem Zimbra** com o método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) da classe [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/).
- **Recuperar uma subpasta PST pelo caminho** - Recuperar uma subpasta com o nome especificado da pasta PST atual usando a sobrecarga do método [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2).

## [Aspose.Email para .NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Adicionar um Anexo de Referência a uma Mensagem** - Adicionamos um novo método [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) à classe [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) com os seguintes parâmetros:
  - `name` - o nome do anexo
  - `sharedLink` - um link compartilhado totalmente qualificado para o anexo fornecido pelo serviço web que manipula o anexo
  - `url` - um local de arquivo
  - `providerName` - um nome do provedor do anexo de referência
- **Verificação de Múltiplos Contatos VCard** - Verifique se um arquivo de origem contém vários contatos com o novo método [VCardContact.IsMultiContacts(string filePath)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1).
- **Converter o formato do Calendário ICS para Formatos de Mensagem** - Converter compromissos em objetos de mensagem como MapiMessage e MailMessage.  
- **Opções Adicionais para Salvar Mensagens nos Formatos HTML e MHTML**:
  - [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Obtém ou define a Prioridade atual do objeto Tarefa.
  - [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define se há necessidade de salvar todos os cabeçalhos na saída mhtml ou não.
  - [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Indica que os campos de Tarefa específicos devem ser escritos no html de saída.
- **Definir Tempo Limite para Conversão de Mensagem e Processo de Carregamento** - Limitar o tempo em milissegundos durante a conversão e o carregamento de mensagens, garantindo que o processo não demore mais do que o necessário. Para esse fim, os seguintes recursos foram introduzidos:
  - [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Limita o tempo em milissegundos durante a conversão de uma mensagem.
  - [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Levantado se o tempo esgotar durante a conversão para MailMessage.
  - [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita o tempo em milissegundos durante a conversão de uma mensagem.
  - [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Levantado se o tempo esgotar durante a conversão para MailMessage.

## [Aspose.Email para .NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Obter o Número Total de Itens de Mensagem Contidos na Armazenagem OLM** com o método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class).
- **Determinar se MapiMessage é OFT ou MSG** - Determinar se o MapiMessage foi carregado de um arquivo OFT ou MSG com a nova propriedade [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/).
- **Detectar um Formato de Arquivo NSF**

## [Aspose.Email para .NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

- **Recuperar propriedades da mensagem a partir de MboxMessageInfo** - Acesse as informações sobre mensagens individuais armazenadas em um arquivo mbox, como tamanho da mensagem, índice da mensagem, cabeçalhos da mensagem, flags da mensagem e outros metadados relacionados à mensagem. Adicionamos as seguintes propriedades à classe [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class):

Data e Hora Date - Obtém a data da mensagem
MailAddress From - Obtém o endereço de remetente
string Subject - Obtém o assunto da mensagem
MailAddressCollection To - Obtém a coleção de endereços que contém os destinatários da mensagem
MailAddressCollection CC - Obtém a coleção de endereços que contém os destinatários em cópia
MailAddressCollection Bcc - Obtém a coleção de endereços que contém os destinatários em cópia oculta da mensagem

## [Aspose.Email para .NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Obter o número total de itens de mensagem contidos no PST** - Adicionamos o método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) à propriedade [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/).
- **Obter uma Pasta de Feed RSS Padrão no Armazenamento Pessoal**, **Adicionar uma Pasta de Feed RSS Padrão no PST** - Um novo valor RssFeeds foi adicionado ao enum StandardIpmFolder. Agora a Pasta de Feed RSS pode ser facilmente recuperada ou adicionada ao armazenamento.
- **Descriptografar uma Mensagem de Email Armazenada no Formato MAPI** - Adicionamos um método Decrypt à classe MapiMessage:
  - [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Obtém um valor indicando se a mensagem está criptografada.
  - [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Descriptografa esta mensagem (o método procura o usuário e os armazéns do computador atual pelo certificado e chave privada apropriados).
  - [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Descriptografa esta mensagem com um certificado. 
- **Definindo um ID de Produto ao Salvar MapiCalendar em ICS** - Adicionamos a propriedade [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) à classe [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/). 
- **Extrair Mensagens por Identificadores de OLM e MBOX** - Esta é a maneira eficiente de evitar percorrer todo o armazenamento a cada vez para encontrar uma mensagem específica a ser extraída.
- **Determinar se o Anexo é Inline ou Regular** com a propriedade [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) .

## [Aspose.Email para .NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Obter um Tipo de Item MAPI** - Evitar a verificação do valor da propriedade MessageClass toda vez antes da conversão da mensagem.
- **Remover Assinatura do MapiMessage** - Para melhor compatibilidade, o método [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) e a propriedade [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) foram adicionados.
- **Identificando Pastas Predefinidas** - O novo método [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class), [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/), foi introduzido para determinar se uma pasta está dentro de uma pasta predefinida, retornando o valor do enum StandardIpmFolder com base no valor do parâmetro especificado.
- **Verificando o Formato TNEF do Anexo** - A propriedade [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) indica se o anexo da mensagem é uma mensagem formatada em TNEF.

## [Aspose.Email para .NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Renomear um Anexo no MapiMessage** - Agora é possível editar o valor da propriedade [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) nos anexos do MapiMessage.

## [Aspose.Email para .NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **Listar Mensagens com a API Graph** - O novo método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) permite controlar a ordenação das mensagens recuperadas com base nos critérios que você especificar.

## [Aspose.Email para .NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Ler Mensagens de MBOX** - Introduzimos novos recursos para configurar opções de carregamento:
  - A propriedade [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) - Obtém ou define opções de carregamento de email ao analisar um armazenamento Mbox.
  - O método [MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1). O parâmetro EmlLoadOptions especifica opções ao ler mensagens do armazenamento Mbox.

## [Aspose.Email para .NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Obter Informações de Identificação da Mensagem** como UID ou número de sequência usando os seguintes recursos:
  - A classe [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) - Representa informações de identificação sobre uma mensagem em uma caixa de correio.
  - A propriedade [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) - O número de sequência de uma mensagem.
  - A propriedade [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) - O id único de uma mensagem.
  - A propriedade [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) - Representa informações de identificação sobre uma mensagem em uma caixa de correio.

## [Aspose.Email para .NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Preservar o Timestamp Original em arquivos ICS** - Extrair itens de calendário de arquivos PST e salvá-los no formato ICS com o timestamp original usando as seguintes opções:
  - [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opções adicionais ao salvar o MapiCalendar no formato ICS.
  - A propriedade [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite manter o valor original do DateTimeStamp no arquivo de saída.

## [Aspose.Email para .NET 22.5](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-5-release-notes/)

- **Enumerar Mensagens com Suporte a Paginação via Graph Client** - A API fornece suporte à paginação e filtragem para listar mensagens. Isso é muito útil quando a caixa de correio possui um grande número de mensagens e requer muito tempo para recuperar as informações resumidas sobre essas.
- **Modo Assíncrono no Tratamento de Clientes de Email** - Uma nova abordagem para a tarefa inclui os seguintes membros da API:
  - [`IAsyncSmtpClient`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/) - Permite que aplicativos enviem mensagens usando o Protocolo de Transferência de Correio Simples (SMTP).
  - [`SmtpClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/#smtpclientcreateasync-method) - Cria uma nova instância da classe `Aspose.Email.Clients.Smtp.SmtpClient`.
  - [`IAsyncSmtpClient.SendAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpSend`) parâmetro definido.
  - [`IAsyncSmtpClient.ForwardAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpForward`) argumentos.
  - [`IAsyncImapClient`](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite que aplicativos acessem e manipulem mensagens usando o Protocolo de Acesso a Mensagens da Internet (IMAP).
  - [`ImapClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Cria uma nova instância da classe `Aspose.Email.Clients.Imap.ImapClient`.

## [Aspose.Email para .NET 22.4](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-4-release-notes/)

- **Enviar Email com MailGun e SendGrid Delivery Services** - Criamos uma API unificada que você pode usar para inicializar opções dependendo de qual serviço será usado para enviar mensagens, chamar a instância do cliente necessária usando o construtor, preparar e enviar uma mensagem de email. Também há uma versão assíncrona do método Send.
- **Definir o cabeçalho X-ALT-DESC no arquivo ICS** - Introduzimos uma nova propriedade [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) para definir o cabeçalho X-ALT-DESC.

## [Aspose.Email para .NET 22.3](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-3-release-notes/)

- **Listar Anexos de Mensagem usando o Cliente IMAP** - Obtenha informações sobre anexos como nome, tamanho sem buscar os dados do anexo. Os membros da API envolvidos na operação: 
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfo`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) - Representa informações do anexo.
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfocollection/) - Representa uma coleção de ImapAttachmentInfo. 
  - [`Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/) - Obtém informações sobre cada anexo na mensagem.
- **Buscar Itens com Anexos via Cliente EWS** - Adicionamos o método [`FetchItems(EwsFetchItems options)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method) ao [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#iewsclient-interface). Ele aceita uma instância da classe [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) como um parâmetro para controlar o comportamento do método.

## [Aspose.Email para .NET 22.2](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-2-release-notes/)

- **Adicionando Anexos de Referência**
    Introduzidos membros da API:
  - [`Aspose.Email.ReferenceAttachment`](https://reference.aspose.com/email/net/aspose.email/referenceattachment/#referenceattachment-class) - representa um anexo de referência.
  - [`Aspose.Email.AttachmentPermissionType`](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) - O tipo de permissão de dados associado a um anexo de referência na web.
  - [`Aspose.Email.AttachmentProviderType`](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) - O tipo de serviço web que manipula o anexo.
- **Recuperar classe de mensagem** - Adicionamos a propriedade [MessageClass](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/messageclass/#exchangemessageinfomessageclass-propertyм) à classe [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/#exchangemessageinfo-class) para recuperar a classe de cada mensagem na coleção de uma pasta pública, após estabelecer uma conexão com um cliente EWS.