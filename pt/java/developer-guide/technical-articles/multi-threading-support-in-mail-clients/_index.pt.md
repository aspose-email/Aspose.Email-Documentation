---
title: "Suporte a multi-threading em clientes de email"
url: /pt/java/suporte-a-multi-threading-em-clientes-de-email/
weight: 250
type: docs
---


Clientes de email como [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) e [Pop3Client](https://apireference.aspose.com/email/java/com.aspose.email/Pop3Client) permitem que os usuários os utilizem em um ambiente de multi-threading. Clientes de email permitem ter uma ou mais conexões com um servidor. Para gerenciar um conjunto de conexões dentro dos clientes, é utilizado um pool de conexões. A quantidade de conexões que podem ser criadas e usadas ao mesmo tempo é limitada pela propriedade CredentialsByHostClient.MaxConnectionsPerServer. Essa propriedade pode ser definida como 1 ou um valor maior. Por padrão, essa propriedade é igual a 10. A fila de comandos foi implementada para a conexão a fim de suportar operações de multi-threading. Os comandos implementam as operações mais simples definidas no protocolo, como Noop, Authenticate e assim por diante. O usuário pode iniciar a execução de uma quantidade maior de comandos do que a quantidade de conexões disponíveis. Porém, serão executados apenas quando o cliente puder criar uma conexão para a operação.
## **Métodos de Uso de Clientes de Email em Ambiente de Multi-Threading**
Clientes de email têm o seguinte comportamento:

**1.** No caso de MaxConnectionsPerServer = 1, o cliente cria 1 conexão, realiza autenticação e autorização. Essa conexão é mantida em estado ativo até o momento em que o cliente for descartado. Todas as operações de diferentes threads são direcionadas a uma fila de comandos colocada na conexão principal.

**2.** No caso de MaxConnectionsPerServer > 1, o cliente cria a quantidade necessária de conexões, realiza autenticação e autorização para cada conexão. Uma conexão é reservada como conexão principal. Essa conexão é mantida em estado ativo até o momento em que o cliente for descartado. Todas as outras conexões são criadas e descartadas conforme a demanda. A quantidade máxima de tais conexões é definida pela propriedade MaxConnectionsPerServer, ou seja, por exemplo, se MaxConnectionsPerServer = 2, então uma é reservada como conexão principal, e a segunda conexão é usada como adicional para operações que são executadas em outras threads. Assim, se MaxConnectionsPerServer = 3, a primeira conexão é reservada como conexão principal, e duas outras conexões são usadas como adicionais para operações que são executadas em outras threads. No caso de uma nova solicitação de conexão de uma nova thread, e todas as conexões já estiverem em uso, o cliente aguarda até que o número de conexões usadas seja reduzido. Este é um momento muito importante que esclarece por que o descarte correto das conexões é tão importante.
## **Exemplos**
O usuário pode executar operações em diferentes threads de várias maneiras. Elas podem ser divididas em dois tipos:

**1.** O usuário usa métodos assíncronos (Begin/End) definidos no cliente. Nesse caso, o cliente de email inicia novas threads quando necessário. No cliente, é implementada uma fila de tarefas (por favor, não confunda com a fila de comandos na conexão). A tarefa pode ser executada se a conexão estiver disponível. Assim que a quantidade de conexões usadas se torna menor que o valor limite, o cliente cria uma nova conexão, cria uma thread para a tarefa atual e executa essa tarefa. Exemplo de uso de operações assíncronas:



~~~Java
// Cria um imapclient com host, usuário e senha
ImapClient client = new ImapClient();
client.setHost("dominio.com");
client.setUsername("usuario");
client.setPassword("senha");
client.selectFolder("Caixa de Entrada");

ImapMessageInfoCollection messages = client.listMessages();
IAsyncResult res1 = client.beginFetchMessage(messages.get_Item(0).getUniqueId());
IAsyncResult res2 = client.beginFetchMessage(messages.get_Item(1).getUniqueId());
MailMessage msg1 = client.endFetchMessage(res1);
MailMessage msg2 = client.endFetchMessage(res2);
~~~



**2.** O usuário pode criar threads usando objetos como Thread, ExecutorService ou quaisquer outros objetos destinados a esse propósito. Além disso, o usuário pode usar threads criadas em código de terceiros. Durante isso, o cliente possui dois modelos de comportamento

**a.** Se o usuário não tiver iniciado a criação de conexões adicionais para operações na thread, todas as operações para esta thread serão enviadas para a fila de comandos da conexão principal. Um exemplo de operações em uma thread adicional sem criar uma nova conexão, todas as transações são realizadas via a conexão principal:



~~~Java
/**
 * Cria um serviço executor com um tamanho de pool fixo, que irá expirar
 * após um certo período de inatividade.
 * 
 * @param poolSize O tamanho do pool principal e máximo
 * @param keepAliveTime O tempo de manutenção
 * @param timeUnit A unidade de tempo
 * @return O serviço executor
 */
private static ExecutorService createFixedTimeoutExecutorService(
    int poolSize, long keepAliveTime, TimeUnit timeUnit)
{
    ThreadPoolExecutor e = 
        new ThreadPoolExecutor(poolSize, poolSize,
            keepAliveTime, timeUnit, new LinkedBlockingQueue<Runnable>());
    e.allowCoreThreadTimeOut(true);
    return e;
}

final List<MailMessage> list = new ArrayList<MailMessage>();

ExecutorService executor = createFixedTimeoutExecutorService(1, 1000, TimeUnit.MILLISECONDS);

executor.execute(new Runnable() {
    public void run() {
        client.selectFolder("nomeDaPasta");
        ImapMessageInfoCollection messageInfoCol = client.listMessages();
        for (ImapMessageInfo messageInfo : messageInfoCol) {
            list.add(client.fetchMessage(messageInfo.getUniqueId()));
        }
    }
});
~~~



**b.** Quando o usuário executa o método para criar uma nova conexão para a thread adicional, essa thread é bloqueada até que o valor da cota para novas conexões seja alterado para permitir uma nova conexão. Então uma nova conexão é criada. Essa conexão é definida como a conexão padrão para todas as operações nesta thread. Após todas as operações nesta thread serem concluídas, a conexão deve ser descartada. Para criar novas conexões, use o método CredentialsByHostClient.CreateConnection. Esse método retorna um objeto que implementa a interface IDisposable. Para liberar a conexão, o método Dispose deve ser invocado. A criação e o descarte da conexão devem ser executados dentro da thread onde as operações de email são realizadas. Tentar criar uma nova conexão na thread onde o cliente de email foi criado leva a um erro, porque esta thread, neste momento, não pode ser usada para a criação de uma nova conexão. Além disso, a criação de nova conexão não é possível quando MaxConnectionsPerServer = 1. Um exemplo de código para criar uma nova conexão em uma thread adicional:


~~~Java
final List<MailMessage> list = new ArrayList<MailMessage>();

ExecutorService executor = createFixedTimeoutExecutorService(1, 1000, TimeUnit.MILLISECONDS);

executor.execute(new Runnable() {
    public void run() {
        IConnection connection = client.createConnection();
        try {
            client.selectFolder(connection, "NomeDaPasta");
            ImapMessageInfoCollection messageInfoCol = client.listMessages(connection);
            for (ImapMessageInfo messageInfo : messageInfoCol)
                list.add(client.fetchMessage(connection, messageInfo.getUniqueId()));
        } finally {
            connection.dispose();
        }
    }
});
~~~
## **Recomendações**
Vale ressaltar que se o usuário enviar todos os comandos para a conexão principal, pode surgir uma situação em que comandos de diferentes threads sejam misturados. O usuário deve entender quais comandos são dependentes de sua sequência e tomar medidas para a sincronização desses comandos. Também é necessário considerar a possibilidade de executar comandos em diferentes sessões (IMAP/POP3). As operações mais demoradas, como FetchMessage, AppendMessage e Send, provavelmente fazem sentido serem executadas com uma nova thread e uma nova conexão. Mas operações rápidas como Delete fazem sentido serem realizadas com a conexão principal. Por favor, note que a inicialização de uma nova conexão é uma operação suficientemente demorada.