---
title: "Ler arquivo OLM do Outlook para Mac e obter informações de pastas e subpastas"
url: /pt/python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM (Arquivo de Arquivamento do Outlook para Mac) é um formato de arquivo associado ao Microsoft Outlook para Mac. É usado para arquivar e armazenar mensagens de e-mail, contatos, itens de calendário, tarefas e outros dados do Outlook em computadores Mac. Os arquivos OLM servem como um formato de backup ou arquivamento, permitindo que os usuários salvem seus dados do Outlook para Mac para referência futura ou migração. É importante notar que os arquivos OLM são específicos do Outlook para Mac e não são compatíveis com o formato de arquivo PST (Tabela de Armazenamento Pessoal) usado pelo Outlook no Windows. Se você precisar transferir dados do Outlook entre diferentes plataformas, ferramentas de conversão serão úteis. Aspose.Email oferece tais ferramentas, incluindo abertura, leitura e outras funcionalidades para trabalhar com arquivos OLM.

## **Abrindo arquivos no formato OLM**

Os arquivos no formato OLM podem ser abertos de duas maneiras:

- usando o construtor
- usando o método 'from_file' estático

### **Abrindo arquivos pelo construtor**

Para abrir um arquivo, chame o construtor da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) e passe o nome completo do arquivo ou fluxo como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Abrindo arquivos usando o método estático FromFile**

Para abrir um arquivo, use o método estático 'from_file' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) e passe o nome completo do arquivo ou fluxo como argumento:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Obtendo pastas**

Você pode visualizar e exibir a hierarquia de pastas recuperada de um arquivo OLM usando a função 'print_all_folders'. Ela aceita a propriedade 'folder_hierarchy' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) e um nível de indentação como entrada, e então percorre recursivamente a hierarquia para imprimir o nome de cada pasta juntamente com a indentação apropriada. O exemplo de código abaixo demonstra como usar essa função para exibir a hierarquia de pastas de um arquivo OLM. Ele exibe a lista de todas as pastas em ordem hierárquica:

```py
import aspose.email as ae


def print_all_folders(folder_hierarchy, indent):
    for folder in folder_hierarchy:
        print(f"{indent}{folder.name}")
        print_all_folders(folder.sub_folders, indent + "-")

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_all_folders(olm.folder_hierarchy, "")
```

O exemplo de código acima visa exibir a hierarquia de pastas do arquivo OLM por meio de uma função recursiva de forma mais estruturada e legível. Aspose.Email também possibilita acessar diretamente a estrutura de pastas do arquivo OLM usando o método 'get_folders()' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class).

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Além disso, é possível obter qualquer pasta pelo nome. O exemplo de código a seguir utiliza o método 'get_folder(name, ignore_case)' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class), passando o nome da pasta e a sensibilidade a maiúsculas como parâmetros para recuperar a pasta pelo seu nome:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **Lista de e-mails**

Os trechos de código abaixo demonstram como usar a biblioteca Aspose.Email para ler e extrair os assuntos de e-mails de um arquivo do Outlook para Mac (OLM). A classe [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class), que representa uma pasta, possui os seguintes métodos para obter a lista de e-mails:

- 'enumerate_messages()' - Itera por cada mensagem de e-mail na pasta. Este método retorna mensagens como instâncias da classe [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class), que fornece informações básicas sobre cada mensagem de e-mail, como assunto, remetente, data, etc.
- 'enumerate_mapi_messages()' - Também itera por cada mensagem de e-mail em uma pasta, mas, neste caso, retorna mensagens como instâncias da classe [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class), que representa uma mensagem de e-mail de forma mais detalhada e específica do MAPI. Isso fornece acesso a uma ampla gama de propriedades e detalhes da mensagem de e-mail, permitindo um processamento mais avançado e especializado.

### **Usando o método EnumerateMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    print(message_info.subject)
```

### **Usando o método EnumerateMapiMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for msg in folder.enumerate_mapi_messages():
    msg.save(f"{msg.subject}.msg")
```

### **Outras propriedades úteis**

As outras propriedades úteis da classe [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) são:

- 'has_messages' - Obtém um valor indicando se a pasta atual possui mensagens.
- 'message_count' - Obtém a contagem de mensagens.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Contagem de mensagens: {folder.message_count}")
```

### **Obter ou definir a data de modificação de uma mensagem**

Você pode recuperar informações sobre o último tempo de modificação de uma mensagem de e-mail. A propriedade 'modified_date' da classe [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) representa a data e hora em que a mensagem foi modificada pela última vez.

Aqui está um exemplo que demonstra o uso da propriedade:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Extraindo e-mails**

Você pode recuperar os dados reais da mensagem MAPI de um armazenamento de e-mail. O método 'extract_mapi_message(message_info)' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) é usado para extrair a mensagem MAPI do armazenamento com base nas informações fornecidas na message_info.

O trecho de código abaixo demonstra como usar esse método:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
```

## **Extraindo todos os itens de um e-mail usando a API de travessia**

Você pode extrair todos os itens de um arquivo OLM do Outlook, na medida do possível, sem lançar exceções, mesmo que alguns dados do arquivo original estejam corrompidos. Para realizar isso, use o construtor [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) e o método [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) em vez do método FromFile. O construtor permite definir um método de callback.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de tratamento de exceção. */ }))
```
O método de callback torna disponíveis as exceções de carregamento e travessia.

O método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) retorna 'true' se o arquivo foi carregado com sucesso e a travessia adicional é possível. Se um arquivo estiver corrompido e a travessia não for possível, 'false' é retornado.

```cs
if (olm.Load(fileName))
```

O seguinte trecho de código e as etapas mostram como usar essa API:

1. Crie uma nova instância da classe [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), passando um callback de tratamento de exceções para lidar com quaisquer exceções encontradas durante o processo.
2. Carregue o arquivo OLM chamando o método [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) da instância de OlmStorage.
3. Se o arquivo OLM for carregado com sucesso, obtenha a hierarquia de pastas chamando o método [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) na instância de OlmStorage. Isso retorna uma lista de objetos OlmFolder.
4. Chame o método ExtractItems, passando a instância de OlmStorage e a lista de objetos OlmFolder.
5. No método ExtractItems, itere através de cada pasta na lista de pastas.
6. Se a pasta contiver mensagens (e-mails), imprima o nome da pasta no console usando Console.WriteLine(folder).
7. Itere através das mensagens na pasta atual chamando o método EnumerateMessages na instância de OlmStorage, passando a pasta atual como argumento.
8. Imprima o assunto de cada mensagem no console usando Console.WriteLine(msg.Subject).
9. Se a pasta tiver subpastas, chame recursivamente o método ExtractItems novamente, passando a instância de OlmStorage e as subpastas da pasta atual.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Código de tratamento de exceção. */ }))
{
    if (olm.Load(fileName))
    {
        var folderHierarchy = olm.GetFolders();
        ExtractItems(olm, folderHierarchy);
    }
}

private static void ExtractItems(OlmStorage olm, List<OlmFolder> folders)
{
    foreach (var folder in folders)
    {
        if (folder.HasMessages)
        {
            Console.WriteLine(folder);

            foreach (var msg in olm.EnumerateMessages(folder))
            {
                Console.WriteLine(msg.Subject);
            }
        }

        if (folder.SubFolders.Count > 0)
        {
            ExtractItems(olm, folder.SubFolders);
        }
    }
}
```
## **Extrair mensagens do OLM por identificadores**

Para acessar os dados da mensagem MAPI, você pode usar a propriedade 'entry_id' para obter o identificador único (Entry ID) de uma mensagem usando a classe [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class). Em seguida, você pode utilizar o método 'extract_mapi_message(id)' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class), passando o entry ID como parâmetro para recuperar a mensagem MAPI associada a esse entry ID específico. O seguinte trecho de código demonstra o uso desses recursos:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Obter caminho da pasta**

Você também pode obter o caminho hierárquico ou a localização da pasta dentro do arquivo OLM do Outlook. Aspose.Email fornece a propriedade 'path' da classe [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) que retorna o caminho da pasta. O seguinte trecho de código demonstra o uso dessa propriedade:

```py
import aspose.email as ae


def print_path(storage, folders):
    for folder in folders:
        # imprime o caminho da pasta atual
        print(folder.path)

        if folder.sub_folders:
            print_path(storage, folder.sub_folders)


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_path(olm, olm.folder_hierarchy)
```

## **Contar o número de itens na pasta**

Aspose.Email oferece a capacidade de contar o número total de mensagens de e-mail contidas em uma pasta específica de um arquivo OLM do Outlook. A propriedade 'message_count' da classe [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) retorna a contagem total de itens (mensagens de e-mail) armazenados em uma pasta específica no arquivo OLM. O seguinte trecho de código demonstra o uso dessa propriedade:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Contagem de Mensagens [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Obter contagem total de itens do OlmStorage**

O método 'get_total_items_count()' da classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) retorna o número total de itens de mensagem contidos no armazenamento OLM.
  
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Recuperar cores de categorias do Outlook**

Com o Aspose.Email, você pode facilmente recuperar e utilizar as cores de categoria associadas às categorias de itens do Outlook armazenadas em arquivos OLM. A classe [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) permite acessar os nomes das categorias e suas respectivas cores representadas em formato hexadecimal. A classe [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) possui o método 'GetCategories()' para recuperar uma lista de categorias do armazenamento OLM. Implementando o trecho de código abaixo, você pode recuperar facilmente todas as categorias utilizadas de um arquivo de armazenamento OML e acessar o nome da categoria juntamente com sua cor.

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
    
    for category in categories:
        print(f"Nome da categoria: {category.Name}")
        
        # A cor é representada como um valor hexadecimal: #rrggbb
        print(f"Cor da categoria: {category.Color}")
```

Além disso, você pode recuperar a cor da categoria associada a mensagens específicas iterando pelas mensagens em uma pasta e acessando a cor da categoria correspondente com base no nome da categoria.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Nome da categoria: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Cor da categoria: {categoryColor}")
```