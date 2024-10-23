---
title: "Detectando Novas Mensagens de Email no Servidor POP3"
url: /pt/net/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---


Com contas POP3, você pode deixar mensagens no servidor ao baixá-las e lê-las. Deixar emails no servidor significa que eles estão disponíveis para outros aplicativos e indivíduos, por exemplo, usuários que acessam seu email de vários dispositivos. Ou você pode querer baixar apenas mensagens que atendem a alguns critérios especiais, por exemplo, mensagens com uma linha de assunto específica. Para gerenciar emails, você pode:

- Ler todas as mensagens do servidor de email POP3 usando Aspose.Email.
- Baixar as mensagens para seu banco de dados local.

As mensagens não são deletadas, mas permanecem no servidor. Da primeira vez que é executado, esse processo funciona bem. Todas as mensagens necessárias são baixadas para o banco de dados. Mas da segunda vez que é executado, as mesmas mensagens são baixadas porque ainda estão no servidor de email. Isso causa registros duplicados. Para resolver esse problema, use a propriedade [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/net/email/aspose.email.clients.pop3/pop3messageinfo/properties/uniqueid) para verificar se uma mensagem já foi baixada. O ID único da mensagem deve ser armazenado no banco de dados: é a chave de pesquisa para detectar novas mensagens.
## **Detectando Novas Mensagens**
Para identificar novos emails a partir de uma lista de emails em um servidor POP3:

1. Conecte-se ao servidor.
1. Obtenha uma lista de emails.
1. Conecte-se ao banco de dados.
1. Obtenha uma lista de emails.
1. Compare as listas.
1. Salve novos emails no banco de dados.

O processo é mais rápido quando você:

1. Busca todos os IDs únicos das mensagens em uma tabela hash.
1. Busca na tabela hash em vez do banco de dados para cada mensagem de email em um loop foreach(…).

Em vez de consultar o banco de dados para cada mensagem, exigindo muitas chamadas ao banco de dados, este método requer apenas uma chamada. O seguinte trecho de código mostra como detectar novas mensagens de email no servidor POP3.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-DetectingNewMessages-DetectingNewMessages.cs" >}}