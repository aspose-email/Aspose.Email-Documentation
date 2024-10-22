---
title: "Filtrar Mensagens do Servidor Usando Cliente IMAP"
url: /pt/python-net/filter-messages-from-server-using-imap-client/
weight: 30
type: docs
---


A classe ImapClient fornece o método ListMessages() que obtém todas as mensagens de uma caixa de entrada. Para obter apenas mensagens que correspondem a alguma condição, use o método sobrecarregado ListMessages() que aceita MailQuery como argumento. A classe MailQuery fornece várias propriedades para especificar as condições, por exemplo, data, assunto, remetente, destinatário e assim por diante. O primeiro exemplo ilustra como filtrar mensagens com base na data e no assunto. Também mostramos como filtrar outros critérios e como construir consultas mais complexas. A API também oferece a capacidade de aplicar critérios de pesquisa que fazem distinção entre maiúsculas e minúsculas para corresponder a critérios de filtragem exatos. A API também permite especificar a codificação da string de pesquisa para filtrar mensagens da caixa de entrada.
## **Filtrando Mensagens da Caixa de Entrada**
1. Conectar e fazer login em um servidor IMAP
1. Criar uma instância de MailQuery e definir as propriedades
1. Chamar o `ImapClient.ListMessages(MailQuery query)` método e passar o MailQuery com os parâmetros para obter apenas mensagens filtradas.

O seguinte trecho de código mostra como conectar a uma caixa de entrada IMAP e obter mensagens que chegaram hoje e têm a palavra "newsletter" no assunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Obtendo Mensagens que Atendem a Critérios Específicos**

Aspose.Email também torna possível construir critérios de pesquisa complexos para consultar e filtrar mensagens de e-mail. Para isso, utilize a classe [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) e suas propriedades. Os critérios para a recuperação são os seguintes:

- Recuperar mensagens por data de entrega.
- Recuperar mensagens dentro de um intervalo.
- Recuperar mensagens de um remetente específico.
- Recuperar mensagens de um domínio específico.
- Recuperar mensagens para um destinatário específico.

### **Data de hoje**

Para recuperar mensagens por uma data de entrega, use a propriedade 'internal_date' conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Intervalo de datas**

Para recuperar mensagens dentro de um intervalo de datas, use a mesma propriedade 'internal_date' especificando o intervalo de datas conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# E-mails que chegaram nos últimos 7 dias
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Remetente específico**

Para recuperar mensagens de um remetente específico, use a propriedade 'from_address' conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Domínio específico**

Para recuperar mensagens de um domínio específico, use a propriedade 'from_address' conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Destinatário específico**

Para recuperar mensagens para um destinatário específico, use a propriedade 'to' conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Construindo Consultas Complexas**

Às vezes, é necessário satisfazer mais de uma consulta. Aspose.Email torna isso possível combinando consultas em várias declarações. Crie um objeto [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) e use suas propriedades para construir consultas específicas.

### **Combinando Consultas com AND**

O seguinte trecho de código mostra como combinar consultas com AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Combinando Consultas com OR**

O seguinte trecho de código mostra como combinar consultas com OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Filtragem com InternalDate**

A API fornece a capacidade de recuperar uma lista de mensagens do servidor que atendem às condições especificadas. O exemplo de código abaixo mostra como construir uma consulta sobre as condições "data interna" e "assunto contém". A "data interna" refere-se à data e hora em que uma mensagem de e-mail foi recebida ou adicionada ao servidor de e-mail e pode ser definida usando a propriedade 'internal_date' da classe [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class). 


```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Defina as condições, Assunto contém "Newsletter", E-mails que chegaram hoje
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Construa a consulta e obtenha a lista de mensagens
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Data Interna: {info.internal_date}")
```
O código imprime a data interna de cada mensagem que atende às condições especificadas.

## **Filtrar Mensagens por Flags de Palavra-Chave Personalizadas**

A biblioteca Aspose.Email permite criar uma consulta para pesquisar em uma caixa de entrada IMAP por e-mails que contêm flags de palavras-chave personalizadas. No exemplo abaixo, as palavras-chave personalizadas usadas são "custom1" e "custom2". Use a classe [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), que é uma ferramenta que permite construir consultas de pesquisa que podem ser usadas para filtrar e-mails ao recuperá-los de um servidor IMAP. Crie um construtor de consulta. Usando o método 'has_flags' do construtor, adicione condições à consulta para incluir apenas e-mails que tenham as palavras-chave de flags IMAP. As palavras-chave personalizadas no IMAP também são conhecidas como flags definidas pelo usuário que podem ser usadas para etiquetar ou marcar e-mails na caixa de entrada para vários propósitos, incluindo categorização, status e mais. O seguinte trecho de código demonstra como criar uma consulta para recuperar e-mails específicos por flags de palavras-chave personalizadas:  

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Filtrar Mensagens Usando Pesquisa Personalizada**

A biblioteca Python pode ser usada para criar uma consulta de pesquisa para uma caixa de entrada IMAP que filtre e-mails com base em um critério de pesquisa personalizada do Gmail, especificamente e-mails que possuem anexos. Crie uma instância de [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), que permite construir consultas de pesquisa IMAP complexas que podem ser usadas para filtrar e-mails de um servidor IMAP. Ao chamar o método 'custom_search', adicione uma string de pesquisa personalizada ao construtor de consultas. A string X-GM-RAW "has:attachment" é um termo de pesquisa específico do Gmail que usa o atributo X-GM-RAW. O Gmail permite o uso de sua sintaxe de pesquisa de webmail em pesquisas IMAP por meio desse atributo. O termo "has:attachment" é um operador de pesquisa do Gmail que encontra todos os e-mails contendo um anexo. O seguinte trecho de código demonstra como filtrar e-mails de acordo com os critérios definidos (neste caso, todos os e-mails com um anexo):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Aplicando Filtros que Diferenciam Maiúsculas e Minúsculas**

A API também fornece a capacidade de filtrar e-mails da caixa de entrada com base em critérios sensíveis a maiúsculas e minúsculas. Os seguintes métodos da classe [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) fornecem a capacidade de pesquisar e-mails especificando flags sensíveis a maiúsculas e minúsculas.  

- Método `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Método `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

O seguinte trecho de código mostra como implementar essa capacidade em seu projeto:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```