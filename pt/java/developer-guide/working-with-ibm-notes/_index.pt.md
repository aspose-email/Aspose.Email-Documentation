---
title: "Trabalhando com IBM Notes"
url: /pt/java/trabalhando-com-ibm-notes/
weight: 120
type: docs
---


## **Sobre o IBM Notes**
O IBM Notes é o cliente e o IBM Domino é o servidor de uma plataforma de software colaborativo cliente-servidor. O IBM Notes fornece recursos de colaboração como e-mail, calendários, listas de tarefas, gerenciamento de contatos, etc. O arquivo de banco de dados usado pelo IBM Notes é salvo no formato Notes Storage Facility (NSF).
## **Ler mensagens do arquivo de armazenamento NSF**

{{% alert color="primary" %}} 

Observe que a implementação NSF é bastante limitada.
Em geral, é possível enfrentar alguns problemas nos seguintes casos:
 - O arquivo foi criado pela versão 7 do Notes ou superior
 - A compressão LZ1 está sendo usada

{{% /alert %}}

Aspose.Email fornece a classe [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) para ler arquivos de armazenamento NSF. A classe [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) fornece o método [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) que itera sobre as mensagens no arquivo de armazenamento NSF. O seguinte código de exemplo demonstra o uso da classe [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) e do método [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) para ler mensagens do arquivo de armazenamento NSF. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}} 

Por favor, note que apenas a leitura de mensagens está implementada. A leitura de pastas ainda não é suportada devido à falta de especificação.

{{% /alert %}}