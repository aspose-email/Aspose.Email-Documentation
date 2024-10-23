---
title: "Trabalhando com IBM Notes"
url: /pt/net/trabalhando-com-ibm-notes/
weight: 130
type: docs
---


## **Sobre o IBM Notes**

IBM Notes é um cliente e IBM Domino é um servidor de uma plataforma de software colaborativo cliente-servidor. O IBM Notes fornece recursos de colaboração como e-mail, calendários, listas de tarefas, gerenciamento de contatos, etc. O arquivo de banco de dados utilizado pelo IBM Notes é salvo no formato Notes Storage Facility (NSF).

## **Detectando se um arquivo está no formato NSF**

O exemplo de código abaixo mostrará como reconhecer o formato de arquivo NSF:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Ler mensagens do arquivo de armazenamento NSF**

{{% alert color="primary" %}}

Observe que a implementação do NSF é bastante limitada.
Em geral, é possível enfrentar alguns problemas nos seguintes casos:

1. O arquivo foi criado pela versão 7 do Notes ou superior
  
2. A compressão LZ1 é utilizada

{{% /alert %}}

Aspose.Email fornece a classe [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) para ler arquivos de armazenamento NSF. A classe [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) fornece o método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) que itera sobre as mensagens no arquivo de armazenamento NSF. O seguinte código de exemplo demonstra o uso da classe [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) e do método [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) para ler mensagens do arquivo de armazenamento NSF.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}} 

Observe que apenas a leitura de mensagens está implementada. A leitura de pastas ainda não é suportada devido à falta de especificação.

{{% /alert %}}