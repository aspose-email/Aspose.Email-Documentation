---
title: "Detectando Novas Mensagens de Email no Servidor POP3"
url: /pt/java/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---

Com contas POP3, você pode deixar mensagens no servidor ao baixá-las e lê-las. Deixar emails no servidor significa que eles estão disponíveis para outros aplicativos e indivíduos, por exemplo, usuários que acessam seu email de vários dispositivos. Ou você pode querer apenas baixar mensagens que atendam a alguns critérios especiais, por exemplo, mensagens com um assunto específico. Para gerenciar emails, você pode:

- Ler todas as mensagens do servidor de email POP3 usando Aspose.Email.
- Baixar as mensagens para o seu banco de dados local.

As mensagens não são excluídas, mas permanecem no servidor. Na primeira vez que é executado, esse processo funciona bem. Todas as mensagens necessárias são baixadas para o banco de dados. Mas na segunda vez que é executado, as mesmas mensagens são baixadas porque ainda estão no servidor de email. Isso causa registros duplicados. Para resolver esse problema, use a propriedade [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/email/java/com.aspose.email/Pop3MessageInfo#getUniqueId\(\)) para verificar se uma mensagem já foi baixada. O ID exclusivo da mensagem deve ser armazenado no banco de dados: é a chave de pesquisa para detectar novas mensagens.
## **Detectando Novas Mensagens**
Para identificar novos emails a partir de uma lista de emails em um servidor POP3:

1. Conecte-se ao servidor.
2. Obtenha uma lista de emails.
3. Conecte-se ao banco de dados.
4. Obtenha uma lista de emails.
5. Compare as listas.
6. Salve novos emails no banco de dados.

O processo é mais rápido quando você:

1. Busca todos os IDs exclusivos das mensagens em uma tabela hash.
2. Pesquisa a tabela hash em vez do banco de dados para cada mensagem de email em um loop for(…).

Em vez de consultar o banco de dados para cada mensagem, o que requer muitas chamadas ao banco de dados, esse método requer apenas uma chamada. O seguinte trecho de código mostra como detectar novas mensagens de email no servidor POP3.

~~~Java
public static void run() {
    try {
        // Connect to the POP3 mail server and check messages.
        Pop3Client pop3Client = new Pop3Client("pop.domain.com", 993, "username", "password");

        // List all the messages
        Pop3MessageInfoCollection msgList = pop3Client.listMessages();
        for (Pop3MessageInfo msgInfo : msgList) {
            // Get the POP3 message's unique ID
            String strUniqueID = msgInfo.getUniqueId();

            // Search your local database or data store on the unique ID. If a match is found, that means it's already downloaded. Otherwise download and save it.
            if (searchPop3MsgInLocalDB(strUniqueID) == true) {
                // The message is already in the database. Nothing to do with this message. Go to next message.
            } else {
                // Save the message
                savePop3MsgInLocalDB(msgInfo);
            }
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }

}

private static void savePop3MsgInLocalDB(Pop3MessageInfo msgInfo) {
    // Open the database connection according to your database. Use public properties (for example msgInfo.Subject) and store in database,
    // for example, " INSERT INTO POP3Mails (UniqueID, Subject) VALUES ('" + msgInfo.UniqueID + "' , '" + msgInfo.Subject + "') and Run the query to store in database.
}

private static boolean searchPop3MsgInLocalDB(String strUniqueID) {
    // Open the database connection according to your database. Use strUniqueID in the search query to find existing records,
    // for example, " SELECT COUNT(*) FROM POP3Mails WHERE UniqueID = '" + strUniqueID + "' Run the query, return true if count == 1. Return false if count == 0.
    return false;
}
~~~