---
title: "Suporte a multi-threading em clientes de e-mail"
url: /pt/net/suporte-a-multi-threading-em-clientes-de-email/
weight: 250
type: docs
---

Clientes de e-mail como ImapClient e Pop3Client permitem que os usuários os utilizem em um ambiente de multi-threading. Os clientes de e-mail permitem ter uma ou mais conexões com um servidor. Para gerenciar um conjunto de conexões dentro dos clientes, é utilizado um pool de conexões. A quantidade de conexões que podem ser criadas e utilizadas ao mesmo tempo é limitada pela propriedade CredentialsByHostClient.MaxConnectionsPerServer. Esta propriedade pode ser definida como 1 ou um valor maior. Por padrão, esta propriedade é igual a 10. Uma fila de comandos foi implementada para a conexão a fim de suportar operações de multi-threading. Os comandos implementam as operações mais simples definidas no protocolo, como Noop, Authenticate e assim por diante. O usuário pode iniciar a execução de uma quantidade maior de comandos do que a quantidade de conexões disponíveis. Mas eles só serão executados quando o cliente for capaz de criar uma conexão para a operação.
## **Métodos de uso de clientes de e-mail em um ambiente de multi-threading**
Os clientes de e-mail têm o seguinte comportamento:

**1.** No caso de MaxConnectionsPerServer = 1, o cliente cria 1 conexão, realiza autenticação e autorização. Esta conexão é mantida em estado de trabalho até o momento em que o cliente for descartado. Todas as operações de diferentes threads são direcionadas a uma fila de comandos colocada na conexão principal.

**2.** No caso de MaxConnectionsPerServer > 1, o cliente cria a quantidade necessária de conexões, realiza autenticação e autorização para cada conexão. Uma conexão é reservada como a conexão principal. Esta conexão é mantida em estado de trabalho até o momento em que o cliente for descartado. Todas as outras conexões são criadas e descartadas conforme a demanda. A quantidade máxima de tais conexões é definida pela propriedade MaxConnectionsPerServer, ou seja, por exemplo, se MaxConnectionsPerServer = 2, então uma é reservada como conexão principal, e a segunda conexão é usada como adicional para operações que são executadas em outras threads. De acordo com isso, se MaxConnectionsPerServer = 3, então a primeira conexão é reservada como conexão principal, e as duas outras conexões são usadas como adicionais para operações que são executadas em outras threads. No caso de uma nova solicitação de conexão surgir de uma nova thread, e todas as conexões já estiverem em uso, o cliente aguarda até que o número de conexões utilizadas seja reduzido. Este é um momento muito importante que esclarece por que o descarte correto de conexões é tão importante.
## **Exemplos**
O usuário pode executar operações em diferentes threads de várias maneiras. Elas podem ser divididas em dois tipos:

**1.** O usuário utiliza métodos assíncronos (Begin/End) definidos no cliente. Nesse caso, o cliente de e-mail inicia novas threads quando necessário. No cliente, é implementada uma fila de tarefas (por favor, não confunda com a fila de comandos na conexão). A tarefa pode ser executada se a conexão estiver disponível. Uma vez que a quantidade de conexões utilizadas se torne menor que o valor limite, o cliente cria uma nova conexão, cria uma thread para a tarefa atual e executa essa tarefa. Exemplo de uso de operações assíncronas:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmail.cs" >}}



**2.** O usuário pode criar threads usando objetos como Thread, ThreadPool, Task ou qualquer outro objeto destinado a esse propósito. O usuário também pode utilizar threads criadas em código de terceiros. Durante isso, o cliente possui dois modelos de comportamento

**a.** Se o usuário não criar conexões adicionais para operações na thread, todas as operações para essa thread serão enviadas para a fila de comandos da conexão principal. Um exemplo de operações em uma thread adicional sem criar uma nova conexão, todas as transações são realizadas através da conexão principal:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool.cs" >}}



**b.** Quando o usuário executa um método para criar uma nova conexão para a thread adicional, essa thread é bloqueada até que o valor da cota para novas conexões seja alterado para permitir uma nova conexão. Então, uma nova conexão é criada. Esta conexão é definida como a conexão padrão para todas as operações nesta thread. Após todas as operações nesta thread serem concluídas, a conexão deve ser descartada. Para criar novas conexões, utilize o método CredentialsByHostClient.CreateConnection. Esse método retorna um objeto que implementa a interface IDisposable. Para liberar a conexão, o método Dispose deve ser invocado. A criação e o descarte de conexões devem ser executados dentro da thread onde as operações de e-mail são realizadas. A tentativa de criar uma nova conexão na thread onde o cliente de e-mail foi criado resulta em um erro, pois essa thread, naquele momento, não pode ser usada para a criação de uma nova conexão. Além disso, a criação de uma nova conexão não é possível quando MaxConnectionsPerServer = 1. Um exemplo de código de criação de uma nova conexão em uma thread adicional:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool1.cs" >}}
## **Recomendações**
Vale ressaltar que se o usuário enviar todos os comandos para a conexão principal, pode surgir uma situação em que comandos de diferentes threads sejam misturados. O usuário deve entender quais comandos dependem de sua sequência e tomar medidas para sincronização desses comandos. Também é necessário considerar a possibilidade de executar comandos em diferentes sessões (IMAP/POP3). As operações mais demoradas, como FetchMessage, AppendMessage e Send, provavelmente fazem sentido serem executadas com uma nova thread e uma nova conexão. Mas operações rápidas como Delete fazem sentido serem executadas com a conexão principal. Observe que a inicialização de uma nova conexão é uma operação bastante demorada.