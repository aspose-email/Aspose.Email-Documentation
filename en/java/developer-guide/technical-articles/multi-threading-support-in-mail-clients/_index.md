---
title: Multi-threading support in mail clients
ArticleTitle: Multi-threading support in mail clients
type: docs
weight: 250
url: /java/multi-threading-support-in-mail-clients/
---


Mail clients like [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) and [Pop3Client](https://apireference.aspose.com/email/java/com.aspose.email/Pop3Client) allow users to use them in multi-threading environment. Mail clients allow to have one or more connections with a server. To manage a set of connections inside of clients is used connection pool. Quantity of connections which can be created and used at the same time, are limited by the property CredentialsByHostClient.MaxConnectionsPerServer. This property may be set to 1 or greater value. By default this property is equal 10. Commands queue has been implemented for the connection to support multi-threading operations. Commands implement simplest operations defined in the protocol, such like Noop, Authenticate and so on. User may start execution greater quantity of commands than quantity available connections. But executed they will be only when client will able to create connection for operation.
## **Methods of Using Mail Clients in Multi-Threading Environment**
Email clients have the following behavior:

**1.** In case of MaxConnectionsPerServer = 1 client creates 1 connection, performs authentication and authorization. This connection is supported in working state till the moment when the client will be disposed. All operations from different threads are directed in one commands queue placed in main connection.

**2.** In case of MaxConnectionsPerServer > 1 client creates needed quantity of connections, performs authentication and authorization for every connection. One connection is reserved as main connection. This connection is supported in working state till the moment when the client will be disposed. All other connections are created and disposed by demand. Maximal quantity of such connections are defined by the property MaxConnectionsPerServer, i.e. for instance if MaxConnectionsPerServer = 2 then one is reserved as main connection, and second connection uses as additional for operations which are executed in other threads. Accordingly if MaxConnectionsPerServer = 3 then first connection is reserved as main connection, and two other connections are used as additional for operations which are executed in other threads. In case if comes next request for connection from new thread, and all connections is already in use, client awaits till number of used connections will not be decreased. This is very important moment that clarifies why correct disposing of connections is so important.
## **Examples**
User may execute operations in different threads in several ways. They can be divided to two types:

**1.** User uses asynchronous (Begin/End) methods defined in the client. In this case the mail client launches new threads when needed. In the client is implemented tasks queue (please, do not be confused with commands queue in connection). Task may be executed if connection is available. Once quantity of used connections becomes less then limit value, client creates new connection, creates thread for current task and executes this task. Example of using asynchronous operations:



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



**2.** User may create threads using such objects as Thread, ExecutorService or any other objects for this purpose intended. Also user may use threads created in third-party code. During this client has two models of behavior

**a.** If the user has not taken the creation of additional connections for operations in the thread, all operations for this thread will be sent to the command queue to the main connection. An example of operations in an additional thread without creating a new connection, all transactions are made via the main connection:



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



**b.** When user runs method to create a new connection for additional thread, this thread is blocked till quota value for new connections will be changed so to allow new connection. Then new connection is created. This connection is set as default connection for all operations in this thread. After all operations in this thread are completed connection must be disposed. To create new connections use CredentialsByHostClient.CreateConnection method. This method returns an object which implements the IDisposable interface. To release connection Dispose method must be invoked. Creation and disposing connection must be executed inside the thread where mail operations are executed. Attempt to create new connection in the thread where mail client has been created leads to an error, because this thread at this moment cannot be used for creation of new connection. Also creation of new connection is not possible when MaxConnectionsPerServer = 1. A code example of creating a new connection additional thread:


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
It is worth noting that if the user sends all commands to the main connection, a situation may arise when commands from different threads are mixed. The user should understand which commands are dependent on their sequence, and to take measures for synchronization of such commands. It is also necessary to consider the possibility of executing commands in different sessions (IMAP/POP3). The most time-consuming operations, such as FetchMessage, AppendMessage and Send. Probably have a sense to perform this operations with new thread and new connection. But quick operations such like Delete have a sense to perform with main connection. Please note that initialization of new connection is enough time-consuming operation.
