---
title: "Recursos de Utilidade"
url: /pt/cpp/utility-features/
weight: 120
type: docs
---

## **Enviando uma Mensagem com Opção de Votação**
O Microsoft Outlook permite que os usuários criem uma pesquisa ao compor uma nova mensagem. Isso é feito incluindo opções de votação, como Sim, Não, Talvez, etc. A classe *FollowUpOptions* oferecida pela Aspose.Email fornece a propriedade *VotingButtons* que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de como criar um *MapiMessage* com opções de votação para criar uma pesquisa e, em seguida, enviar a mensagem usando o cliente do Exchange Web Service (EWS).
### **Criando e Enviando uma Mensagem com Opções de Votação**
O seguinte trecho de código mostra como criar uma nova mensagem e enviá-la com opções de votação.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}


O seguinte trecho de código mostra a definição do método *CreateTestMessage* usado no exemplo acima.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Ignorar ou Ignorar Certificado SSL Inválido ou Expirado**
A Aspose.Email pode lidar com certificados SSL no Exchange Server usando a classe [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Se o certificado SSL expirou ou se tornou inválido, a Aspose.Email lança uma exceção devido ao certificado SSL inválido. Evite tais erros de certificado SSL ignorando-os usando o método mostrado no código abaixo. Registre o manipulador de retorno em seu método main() ou init() e adicione o método abaixo como membro da classe.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Criando mensagens RE e FW a partir de arquivos MSG**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permite que os desenvolvedores criem mensagens RE (Responder/Responder a Todos) e FW (Encaminhar) a partir de uma mensagem fonte. A mensagem fonte é identificada selecionando uma *[ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info)* específica de *[ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection)* obtida através de *[ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e)*. O outro argumento é o *[MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message)* real a ser enviado como mensagem RE ou FW. O seguinte trecho de código mostra como enviar uma mensagem e, em seguida, responder a essa mensagem e encaminhar essa mensagem. Para realizar esta tarefa:

1. Inicialize o objeto *[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)* fornecendo credenciais válidas.
1. Envie algumas mensagens de amostra.
1. Chame os métodos *[Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099)*, *[ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41)* e *[Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27)* para enviar mensagens.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Adicionando Cabeçalhos nas Solicitações EWS**
A API do Aspose.Email permite adicionar cabeçalhos às solicitações do Exchange. Isso pode ser usado para adicionar cabeçalhos às solicitações EWS para diferentes cabeçalhos que podem ser usados para diferentes propósitos. Um exemplo poderia ser adicionar o cabeçalho X-AnchorMailbox, que é usado para gerenciar problemas de limitação no servidor Exchange. O método [AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f) da classe *[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)* é usado para adicionar cabeçalhos às solicitações EWS, conforme mostrado no seguinte trecho de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Trabalhando com Mensagens Unificadas**
A Aspose.Email pode recuperar informações de mensagens unificadas a partir do Exchange Server 2010. Mensagens unificadas, como obter informações de configuração, iniciar uma chamada de saída, recuperar informações de chamadas telefônicas por ID de chamada e desconectar uma chamada telefônica por ID são suportadas atualmente. O seguinte exemplo de código mostra como recuperar informações de configuração de mensagens unificadas do Microsoft Exchange Server 2010.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Obtendo Dicas de E-mail**
O Microsoft Exchange Server adicionou vários novos recursos com o Exchange Server 2010 e 2013. Um deles permite que os usuários obtenham dicas de e-mail ao compor uma mensagem de e-mail. Essas dicas são muito úteis, pois fornecem informações antes que o e-mail seja enviado. Por exemplo, se um endereço de e-mail estiver incorreto na lista de destinatários, uma dica é exibida para informá-lo de que o endereço de e-mail é inválido. As dicas de e-mail também permitem que você veja respostas automáticas fora do escritório antes de enviar um e-mail: o Exchange Server (2010 e 2013) envia a dica de e-mail quando o e-mail está sendo composto, se um ou mais dos destinatários definiram respostas automáticas fora do escritório. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos demonstrados neste artigo. O seguinte trecho de código mostra como usar a classe *[EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client)*, que utiliza os Serviços Web do Exchange, disponíveis no Microsoft Exchange Server 2007 e versões posteriores.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}