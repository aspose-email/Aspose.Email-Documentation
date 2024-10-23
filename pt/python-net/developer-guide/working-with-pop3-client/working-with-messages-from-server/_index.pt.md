---
title: "Trabalhando com Mensagens do Servidor"
url: /pt/python-net/trabalhando-com-mensagens-do-servidor/
weight: 40
type: docs
---

## **Obtendo Informações da Caixa de Correio**
Podemos obter informações sobre a caixa de correio, como o número de mensagens e o tamanho da caixa de correio, usando os métodos GetMailBoxSize() e GetMailBoxInfo().

- O método `GetMailBoxSize()` retorna o tamanho da caixa de correio em bytes.
- O método `GetMailBoxInfo()` retorna um objeto do tipo Pop3MailBoxInfo.

Também é possível obter o número de mensagens usando a propriedade MessageCount e o tamanho usando a propriedade OccupiedSize. O seguinte código de exemplo mostra como obter informações sobre a caixa de correio. Ele demonstra como:

1. Criar um [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Conectar-se a um servidor POP3.
1. Obter o tamanho da caixa de correio.
1. Obter informações da caixa de correio.
1. Obter o número de mensagens na caixa de correio.
1. Obter o tamanho ocupado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Obtendo a contagem de emails na caixa de correio**
O seguinte código de exemplo mostra como contar as mensagens de email em uma caixa de correio.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email permite que os desenvolvedores trabalhem com emails de várias maneiras diferentes. Por exemplo, eles podem recuperar informações de cabeçalho antes de decidir se devem baixar um email. Ou podem recuperar emails de um servidor e salvá-los sem analisá-los (mais rápido) ou após analisá-los (mais lento). Este artigo mostra como recuperar e converter emails.
## **Recuperando Informações dos Cabeçalhos de Email**
Os cabeçalhos de email podem nos fornecer informações sobre uma mensagem de email que podemos usar para decidir se devemos ou não recuperar a mensagem de email completa. Normalmente, as informações do cabeçalho contêm remetente, assunto, data recebida etc. (Os cabeçalhos de email são descritos em detalhes em Personalizando Cabeçalhos de Email. Esse tópico é especificamente sobre envio de email com SMTP, mas as informações de conteúdo do cabeçalho de email permanecem válidas para emails POP3). Os seguintes exemplos mostram como recuperar cabeçalhos de email de um servidor POP3 pelo número de sequência da mensagem.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Recuperando Mensagens de Email**
O componente Aspose.Email.Pop3 fornece a capacidade de recuperar mensagens de email do servidor POP3 e analisá-las em uma instância de MailMessage com a ajuda dos componentes MailMessage. A classe MailMessage contém várias propriedades e métodos para manipular o conteúdo do email. Usando a função FetchMessage da classe Pop3Client, você pode obter uma instância de MailMessage diretamente do servidor POP3. O seguinte código de exemplo mostra como recuperar uma mensagem de email completa do servidor POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Recuperando Informações Resumidas da Mensagem usando ID Único**
O Cliente POP3 da API pode recuperar informações resumidas da mensagem do servidor usando o ID único da mensagem. Isso fornece acesso rápido às informações resumidas da mensagem sem precisar primeiro recuperar a mensagem completa do servidor. O seguinte código de exemplo mostra como recuperar informações resumidas da mensagem.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Listando Mensagens com MultiConexão**

Para operações com alta carga, Aspose.Email oferece a propriedade 'use_multi_connection' da classe [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para usar várias conexões ao recuperar emails. No entanto, usar este modo não necessariamente leva ao aumento da performance. O seguinte código de exemplo mostra como estabelecer uma conexão com um servidor POP3, configurar o cliente para permitir até 5 conexões simultâneas e habilitar o modo de multi-conexão para recuperar informações sobre as mensagens presentes no servidor:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Buscando Mensagens do Servidor e salvando no Disco**
### **Salvar Mensagem no Disco sem Análise**
Se você quiser baixar mensagens de email do servidor POP3 sem analisá-las, use a função SaveMessage da classe Pop3Client. A função SaveMessage não analisa a mensagem de email, portanto, é mais rápida que a função FetchMessage. O seguinte código de exemplo mostra como salvar uma mensagem pelo seu número de sequência, neste caso o número 1. O método SaveMessage salva a mensagem no formato EML original sem analisá-la.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Analisar Mensagem Antes de Salvar**

Use o método 'fetch_message' do objeto cliente criado usando a classe [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para recuperar a mensagem com um número de sequência específico. O código de exemplo abaixo demonstra como recuperar uma mensagem específica e salvá-la usando seu assunto como nome do arquivo chamando o método 'save' no objeto msg:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Buscar a mensagem pelo seu número de sequência e salvar a mensagem usando seu assunto como nome do arquivo
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Filtrando Mensagens por Remetente, Destinatário ou Data**
A classe Pop3Client, descrita na Conexão a um Servidor POP3, fornece o método list_messages() que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que atendam a alguma condição, use o método ListMessages() sobrecarregado, que recebe MailQuery como argumento. A classe MailQuery fornece várias propriedades para especificar as condições da consulta, por exemplo, data, assunto, remetente, destinatário e assim por diante. A classe MailQueryBuilder é usada para construir a expressão de busca. Primeiro, todas as condições e restrições são definidas e, em seguida, a MailQuery é preenchida com a consulta desenvolvida pelo MailQueryBuilder. O objeto da classe MailQuery é usado pelo Pop3Client para extrair as informações filtradas do servidor. Este artigo mostra como filtrar mensagens de email de uma caixa de correio. O primeiro exemplo ilustra como filtrar mensagens com base na data e no assunto. Também mostramos como filtrar com base em outros critérios e como construir consultas mais complexas. Também mostra a aplicação de filtros de Data e Hora para recuperar emails específicos da caixa de correio. Além disso, também mostra como aplicar filtragem com distinção entre maiúsculas e minúsculas.
### **Filtrando Mensagens da Caixa de Correio**
Para filtrar mensagens de uma caixa de correio:

1. Conecte-se e faça login em um servidor POP3.
1. Crie uma instância de MailQuery e defina as propriedades desejadas.
1. Chame o método `Pop3Client.list_messages(MailQuery query)` e passe a MailQuery como parâmetro para obter apenas as mensagens filtradas.

O seguinte código de exemplo mostra como conectar-se a uma caixa de correio POP3 e obter mensagens que chegaram hoje e que contêm a palavra "newsletter" no assunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Obtendo Mensagens que Atendem a Critérios Específicos**

Aspose.Email também possibilita a construção de critérios de busca complexos para consultar e filtrar mensagens de email. Para isso, use a classe [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) e suas propriedades. Os critérios para busca são os seguintes:

- Buscar mensagens por data de entrega.
- Buscar mensagens dentro de um intervalo.
- Buscar mensagens de um remetente específico.
- Buscar mensagens de um domínio específico.
- Buscar mensagens para um destinatário específico.

#### **Data de Hoje**

Para buscar mensagens por uma data de entrega, use a propriedade 'internal_date' como mostrado no código de exemplo abaixo:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Intervalo de Datas**

Para buscar mensagens dentro de um intervalo de datas, use a mesma propriedade 'internal_date' especificando o intervalo de datas como mostrado no código de exemplo abaixo:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails que chegaram nos últimos 7 dias
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Remetente Específico**

Para buscar mensagens de um remetente específico, use a propriedade 'from_address' como mostrado no código de exemplo abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Domínio Específico**

Para buscar mensagens de um domínio específico, use a propriedade 'from_address' como mostrado no código de exemplo abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Destinatário Específico**

Para buscar mensagens para um destinatário específico, use a propriedade 'to' como mostrado no código de exemplo abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Construindo Consultas Complexas**

Às vezes, é necessário satisfazer mais de uma consulta. Aspose.Email torna isso possível combinando consultas em várias declarações. Crie um objeto [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) e use suas propriedades para construir consultas específicas.

#### **Combinando Consultas com AND**

O seguinte código de exemplo mostra como combinar consultas com AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Combinando Consultas com OR**

O seguinte código de exemplo mostra como combinar consultas com OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Aplicando Filtros Sensíveis a Maiúsculas e Minúsculas**

A API também fornece a capacidade de filtrar emails da caixa de correio com base em um critério sensível a maiúsculas e minúsculas. Os seguintes métodos da classe [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) fornecem a capacidade de buscar emails especificando flags sensíveis a maiúsculas e minúsculas.  

- Método `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

O seguinte código de exemplo mostra como implementar essa capacidade em seu projeto:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```