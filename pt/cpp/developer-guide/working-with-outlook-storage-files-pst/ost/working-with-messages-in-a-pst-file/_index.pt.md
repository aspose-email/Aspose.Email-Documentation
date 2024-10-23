---
title: "Trabalhando com Mensagens em um Arquivo PST"
url: /pt/cpp/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---

## **Adicionando Mensagens a Arquivos PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar mensagens a subpastas de um arquivo PST que você criou ou carregou. Este artigo adiciona duas mensagens do disco à subpasta Caixa de Entrada de um PST. Use as classes PersonalStorage e FolderInfo para adicionar mensagens a arquivos PST. Para adicionar mensagens à pasta Caixa de Entrada de um arquivo PST:

1. Crie uma instância da classe FolderInfo e carregue-a com o conteúdo da pasta Caixa de Entrada.
1. Adicione mensagens do disco à pasta Caixa de Entrada chamando o método FolderInfo.AddMessage(). A classe FolderInfo expõe o método AddMessages que permite adicionar um grande número de mensagens à pasta, reduzindo as operações de entrada/saída para o disco e melhorando o desempenho. Um exemplo completo pode ser encontrado abaixo, em Adicionando Mensagens em Massa.

Os trechos de código abaixo mostram como adicionar mensagens a uma subpasta PST chamada Caixa de Entrada.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMessagesToPSTFiles-AddMessagesToPSTFiles.cpp" >}}
### **Salvando Mensagens Diretamente de PST para Stream**
Para salvar mensagens de um arquivo PST diretamente para um stream, sem extrair o MsgInfo para mensagens, use o método SaveMessageToStream(). O seguinte trecho de código mostra como salvar mensagens diretamente de PST para stream.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveMessagesDirectlyFromPSTToStream-SaveMessagesDirectlyFromPSTToStream.cs" >}}
### **Extraindo n Número de Mensagens de um Arquivo PST**
O seguinte trecho de código mostra como extrair um número especificado de mensagens de um PST. Basta fornecer o índice da primeira mensagem e o número total de mensagens a serem extraídas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractNumberOfMessages-ExtractNnumberOfMessages.cpp" >}}
## **Pesquisar Mensagens e Pastas em um PST por Critério**
Os arquivos de Armazenamento Pessoal (PST) podem conter uma enorme quantidade de dados e procurar dados que atendem a um critério específico em arquivos tão grandes precisa incluir vários pontos de verificação no código para filtrar a informação. Com a classe PersonalStorageQueryBuilder, a Aspose.Email torna possível pesquisar registros específicos em um PST com base em um critério de pesquisa especificado. Um PST pode ser pesquisado por mensagens com base em parâmetros de pesquisa como remetente, destinatário, assunto, importância da mensagem, presença de anexos, tamanho da mensagem e até mesmo ID da mensagem. A PersonalStorageQueryBuilder também pode ser utilizada para pesquisar subpastas.
### **Pesquisando Mensagens e Pastas em PST**
O seguinte trecho de código mostra como usar a classe PersonalStorageQueryBuilder para pesquisar conteúdos em um PST com base em diferentes critérios de pesquisa. Por exemplo, mostra como pesquisar um PST com base em:

- Importância da mensagem.
- Classe da mensagem.
- Presença de anexos.
- Tamanho da mensagem.
- Mensagens não lidas.
- Mensagens não lidas com anexos, e
- pastas com nome de subpasta específico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SearchMessagesAndFoldersInPST-SearchMessagesAndFoldersInPST.cpp" >}}
## **Extrair Anexos sem Extrair Mensagem Completa**
A API Aspose.Email pode ser utilizada para extrair anexos de mensagens PST sem extrair primeiro a mensagem completa. O método ExtractAttachments da classe IEWSClient pode ser utilizado para isso. O seguinte trecho de código mostra como extrair anexos sem extrair a mensagem completa.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractAttachmentsFromPSTMessages-ExtractAttachmentsFromPSTMessages.cpp" >}}
## **Adicionando Arquivos a PST**
A funcionalidade principal do Microsoft Outlook é gerenciar e-mails, calendários, tarefas, contatos e entradas de diário. Além disso, arquivos também podem ser adicionados a uma pasta PST e o PST resultante mantém registro dos documentos adicionados. Aspose.Email fornece a facilidade de adicionar arquivos a uma pasta da mesma forma, além de adicionar mensagens, contatos, tarefas e entradas do diário ao PST. O seguinte trecho de código mostra como adicionar documentos a uma pasta PST usando Aspose.Email.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddFilesToPST-AddFilesToPST.cpp" >}}