---
title: "Поддержка многопоточности в почтовых клиентах"
url: /ru/java/multi-threading-support-in-mail-clients/
weight: 250
type: docs
---


Почтовые клиенты, такие как [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) and [Pop3Client](https://apireference.aspose.com/email/java/com.aspose.email/Pop3Client) разрешить пользователям использовать их в многопоточной среде. Почтовые клиенты позволяют установить одно или несколько подключений к серверу. Для управления набором подключений внутри клиентов используется пул соединений. Количество подключений, которые можно создать и использовать одновременно, ограничено свойством CredentialsByHostClient.MaxConnectionsPerServer. Это свойство может быть равно 1 или большему значению. По умолчанию это свойство равно 10. Для подключения реализована очередь команд для поддержки многопоточных операций. Команды реализуют самые простые операции, определенные в протоколе, такие как Noop, Authenticate и т. д. Пользователь может начать выполнение большего количества команд, чем количество доступных подключений. Но они будут выполнены только тогда, когда клиент сможет создать соединение для операции.
## **Методы использования почтовых клиентов в многопоточной среде**
Почтовые клиенты ведут себя следующим образом:

**1.** В случае MaxConnectionsPerServer = 1 клиент создает 1 соединение, выполняет аутентификацию и авторизацию. Это соединение поддерживается в рабочем состоянии до тех пор, пока клиент не будет удален. Все операции из разных потоков направляются в одну очередь команд, размещенную в основном соединении.

**2.** В случае MaxConnectionsPerServer > 1 клиент создает необходимое количество подключений, выполняет аутентификацию и авторизацию для каждого соединения. Одно соединение зарезервировано в качестве основного. Это соединение поддерживается в рабочем состоянии до тех пор, пока клиент не будет удален. Все остальные соединения создаются и удаляются по запросу. Максимальное количество таких подключений определяется свойством MaxConnectionsPerServer, то есть, например, если maxConnectionsPerServer = 2, то одно соединение зарезервировано в качестве основного соединения, а второе используется в качестве дополнительного для операций, выполняемых в других потоках. Соответственно, если MaxConnectionsPerServer = 3, то первое соединение зарезервировано как основное соединение, а два других соединения используются в качестве дополнительных для операций, выполняемых в других потоках. Если из нового потока поступит следующий запрос на подключение, а все соединения уже используются, клиент ожидает, пока количество используемых подключений не уменьшится. Это очень важный момент, объясняющий, почему правильное удаление подключений так важно.
## **Examples**
Пользователь может выполнять операции в разных потоках несколькими способами. Их можно разделить на два типа:

**1.** Пользователь использует асинхронные методы (начало/конец), определенные в клиенте. В этом случае почтовый клиент запускает новые потоки при необходимости. В клиенте реализована очередь задач (пожалуйста, не путайте с очередью команд при подключении). Задание может быть выполнено при наличии соединения. Как только количество используемых подключений становится меньше предельного значения, клиент создает новое соединение, создает поток для текущей задачи и выполняет эту задачу. Пример использования асинхронных операций:



~~~Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");

ImapMessageInfoCollection messages = client.listMessages();
IAsyncResult res1 = client.beginFetchMessage(messages.get_Item(0).getUniqueId());
IAsyncResult res2 = client.beginFetchMessage(messages.get_Item(1).getUniqueId());
MailMessage msg1 = client.endFetchMessage(res1);
MailMessage msg2 = client.endFetchMessage(res2);
~~~



**2.** Пользователь может создавать потоки, используя такие объекты, как Thread, ExecutorService или любые другие объекты для этой цели. Также пользователь может использовать темы, созданные в стороннем коде. При этом у клиента есть две модели поведения

**a.** Если пользователь не взял на себя создание дополнительных подключений для операций в потоке, все операции для этого потока будут отправлены в очередь команд к основному соединению. Пример операций в дополнительном потоке без создания нового соединения, все транзакции осуществляются через основное соединение:



~~~Java
/**
 * Creates an executor service with a fixed pool size, that will time
 * out after a certain period of inactivity.
 *
 * @param poolSize The core- and maximum pool size
 * @param keepAliveTime The keep alive time
 * @param timeUnit The time unit
 * @return The executor service
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
        client.selectFolder("folderName");
        ImapMessageInfoCollection messageInfoCol = client.listMessages();
        for (ImapMessageInfo messageInfo : messageInfoCol) {
            list.add(client.fetchMessage(messageInfo.getUniqueId()));
        }
    }
});
~~~



**b.** Когда пользователь запускает метод создания нового соединения для дополнительного потока, этот поток блокируется до тех пор, пока значение квоты для новых подключений не будет изменено таким образом, чтобы разрешить новое подключение. Затем создается новое соединение. Это соединение установлено в качестве соединения по умолчанию для всех операций в этом потоке. После завершения всех операций в этом потоке соединение необходимо удалить. Для создания новых подключений используйте метод CredentialsByHostClient.createConnection. Этот метод возвращает объект, реализующий интерфейс IDisposable. Для разблокирования соединения необходимо вызвать метод Dispose. Создание и удаление соединения должны выполняться внутри потока, в котором выполняются почтовые операции. Попытка создать новое соединение в потоке, в котором был создан почтовый клиент, приводит к ошибке, поскольку этот поток в данный момент нельзя использовать для создания нового соединения. Кроме того, создание нового соединения невозможно, если MaxConnectionsPerServer = 1. Пример кода создания дополнительного потока нового соединения:


~~~Java
final List<MailMessage> list = new ArrayList<MailMessage>();

ExecutorService executor = createFixedTimeoutExecutorService(1, 1000, TimeUnit.MILLISECONDS);

executor.execute(new Runnable() {
    public void run() {
        IConnection connection = client.createConnection();
        try {
            client.selectFolder(connection, "FolderName");
            ImapMessageInfoCollection messageInfoCol = client.listMessages(connection);
            for (ImapMessageInfo messageInfo : messageInfoCol)
                list.add(client.fetchMessage(connection, messageInfo.getUniqueId()));
        } finally {
            connection.dispose();
        }
    }
});
~~~
## **Recommendations**
Стоит отметить, что если пользователь отправляет все команды основному соединению, может возникнуть ситуация, когда команды из разных потоков смешиваются. Пользователь должен понимать, какие команды зависят от их последовательности, и принимать меры для синхронизации таких команд. Также необходимо рассмотреть возможность выполнения команд в разных сеансах (IMAP/POP3). Наиболее трудоемкие операции, такие как FetchMessage, AppendMessage и Send. Вероятно, есть смысл выполнить эти операции с новым потоком и новым подключением. Но быстрые операции, такие как Delete, имеет смысл выполнять с основным подключением. Обратите внимание, что инициализация нового соединения — достаточно трудоемкая операция.
