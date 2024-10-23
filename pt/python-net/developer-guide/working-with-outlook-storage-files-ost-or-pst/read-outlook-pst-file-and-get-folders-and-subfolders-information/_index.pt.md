---
title: "Ler Arquivo PST do Outlook e Obter Informações sobre Pastas e Subpastas"
url: /pt/python-net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

Aspose.Email para .NET fornece uma API para ler arquivos PST do Microsoft Outlook. Você pode carregar um arquivo PST do disco ou stream para uma instância da classe PersonalStorage e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens. A API também fornece a capacidade de incluir pastas de busca ao percorrer mensagens das pastas PST.
## **Carregando um Arquivo PST**
Um arquivo PST do Outlook pode ser carregado em uma instância da classe PersonalStorage. O seguinte trecho de código mostra como carregar o arquivo PST.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
```
## **Exibindo Informações do PST**
Após carregar o arquivo PST na classe PersonalStorage, você pode obter informações sobre o nome do arquivo, pasta raiz, subpastas e contagem de mensagens. O seguinte trecho de código mostra como exibir o nome do arquivo PST, pastas e número de mensagens nas pastas.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.py" >}}
```

## **Obter apenas pastas criadas pelo usuário**

Os arquivos PST/OST podem conter pastas que foram criadas por um usuário, ou seja, excluindo todas as pastas IPM padrão. Aspose.Email fornece a capacidade de acessar apenas pastas criadas pelo usuário utilizando a propriedade *only_folders_created_by_user* da classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class). Você pode definir a propriedade *only_folders_created_by_user* como True para obter apenas pastas criadas pelo usuário. O seguinte trecho de código demonstra como você pode usar a propriedade *only_folders_created_by_user* em seu projeto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

query_builder = ae.storage.pst.PersonalStorageQueryBuilder()
query_builder.only_folders_created_by_user.equals(True)

folders = pst.root_folder.get_sub_folders(query_builder.get_query())

for folder in folders:
    print(f"Folder: {folder.display_name}")
```

## **Verificando se a pasta está em uma pasta pré-definida**

O método "get_predefined_type" da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) permite descobrir se uma pasta dentro de um arquivo PST é uma pasta padrão. Pastas padrão (ou pré-definidas), em oposição às pastas criadas pelo usuário, são pastas que são criadas pelo Outlook quando você adiciona uma conta de e-mail, como Caixa de Entrada, Itens Enviados, Rascunhos, Itens Excluídos, Calendário, Tarefas, Notas etc.

O exemplo de código abaixo demonstra como usar este método em um projeto. Se definido como True, retorna o tipo pré-definido para a pasta principal de nível superior. Isso determina se a pasta atual é uma subpasta de uma pasta pré-definida. Se definido como False, retorna o tipo pré-definido para a pasta atual.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders()

for folder in folders:
    print(f"Folder: {folder.display_name}")
    print(f"Is predefined: {folder.get_predefined_type(False) != ae.storage.pst.StandardIpmFolder.UNSPECIFIED}")
    print("-----------------------------------")
```
## **Obtendo e adicionando uma pasta padrão de Feeds RSS no PersonalStorage**

Aspose.Email fornece funcionalidade para recuperar uma referência a uma pasta pré-definida de Feeds RSS, permitindo aos desenvolvedores acessar e manipular programaticamente os feeds RSS armazenados em um arquivo PST do Outlook. Ao obter uma referência à "pasta de Feeds RSS", os desenvolvedores podem trabalhar com os dados do feed RSS, que podem incluir se inscrever em novos feeds, atualizar feeds existentes ou extrair informações dos feeds.

O valor de RssFeeds no enum StandardIpmFolder normalmente representaria o tipo de pasta pré-definido especificamente projetado para armazenar feeds RSS dentro de um arquivo PST do Outlook. Usando este valor do enum, os desenvolvedores podem direcionar e interagir com a "pasta de Feeds RSS" programaticamente. Os seguintes exemplos de código demonstrarão como implementar este recurso em seu projeto:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```
Para adicionar uma pasta de Feeds RSS, utilize o seguinte trecho de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.create_predefined_folder("RSS Feeds", ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```

## **Analisando Pastas Pesquisáveis**

Aspose.Email fornece uma enumeração [FolderKind](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderkind/#folderkind-enumeration) para trabalhar com diferentes tipos de pastas PST. Além de pastas NORMAIS, ele trabalha com pastas de PESQUISA. Uma pasta de PESQUISA é uma pasta virtual que fornece uma visão de todos os itens de e-mail que correspondem a critérios de pesquisa específicos. Para analisar pastas de PESQUISA, utilize o seguinte trecho de código:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)

# Percorra cada pasta para exibir o nome da pasta e o número de mensagens
for folder in folders:
    print(f"Folder: {folder.display_name}")
    sub_folders = folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)
    for sub_folder in sub_folders:
        print(f"Sub-folder: {folder.display_name}")
```

## **Recuperando Informações da Pasta Pai a partir de MessageInfo**
O seguinte trecho de código mostra como recuperar informações da pasta pai a partir de MessageInfo.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-RetrievingParentFolderInformationFromMessageInfo-RetrievingParentFolderInformationFromMessageInfo.py" >}}
```

## **Recuperando uma subpasta PST pelo caminho**

Para recuperar uma subpasta PST pelo caminho, utilize o método *get_sub_folder* da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Ele recupera uma subpasta específica dentro de um diretório ou sistema de arquivos.

O método leva os seguintes parâmetros:

- **name** - representa o nome da subpasta que precisa ser recuperada. É usado para especificar o nome ou identificador da subpasta que o método deve procurar.

- **ignore_case** - é um valor booleano que determina se o método deve ignorar a sensibilidade a maiúsculas e minúsculas ao comparar o nome da subpasta. Se definido como True, o método considerará a correspondência de nomes sem considerar a capitalização (por exemplo, "pasta" e "Pasta" serão tratados como iguais). Se definido como False, o método realizará uma comparação sensível a maiúsculas e minúsculas.

- **handle_path_separator** - é um valor booleano que especifica se o método deve lidar com o separador de caminho ao procurar pela subpasta. Os separadores de caminho são caracteres usados para separar pastas em um caminho de diretório (por exemplo, `\` no Windows ou `/` no Unix). Se definido como True, o método lidará automaticamente com o separador de caminho, garantindo uma correspondência correta de pastas. Se definido como False, ele tratará o separador de caminho como parte do nome da subpasta, resultando em um comportamento de busca diferente.

O seguinte exemplo de código mostra como recuperar uma subpasta PST pelo caminho:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# Neste exemplo, o método retornará uma pasta chamada 'Jan'
# que está localizada no caminho Inbox\Reports\
# relativo à pasta raiz.
folder = pst.root_folder.get_sub_folder("Inbox\Reports\Jan", True, True)
```