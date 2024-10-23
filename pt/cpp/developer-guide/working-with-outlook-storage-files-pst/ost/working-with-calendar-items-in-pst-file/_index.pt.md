---
title: "Trabalhando com Itens de Calendário em Arquivo PST"
url: /pt/cpp/trabalhando-com-itens-de-calendario-em-arquivo-pst/
weight: 50
type: docs
---

## **Adicionar MapiCalendar ao PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiCalendar à subpasta Calendário de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiCalendar a um PST:

1. Crie um objeto MapiCalendar.
1. Defina as propriedades do MapiCalendar usando um construtor e métodos.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta predefinida (Calendário) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método AddMapiMessageItem().

O seguinte snippet de código mostra como criar um MapiCalendar e, em seguida, adicioná-lo à pasta de calendário de um arquivo PST recém-criado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cpp" >}}
## **Salvar Itens de Calendário do PST para Disco no Formato ICS**
Este artigo mostra como acessar itens de calendário de um arquivo PST do Outlook e salvar o calendário no disco no formato ICS. Use as classes PersonalStorage e MapiCalendar para obter as informações do calendário. Abaixo estão os passos para salvar itens de calendário:

1. Carregue o arquivo PST na classe PersonalStorage.
1. Navegue até a pasta Calendário.
1. Obtenha o conteúdo da pasta Calendário para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método PersonalStorage.ExtractMessage() para obter as informações de contato na classe MapiCalendar.
1. Chame o método MapiCalendar.Save() para salvar o item de calendário no disco no formato ICS.

O programa abaixo carrega um arquivo PST do disco e salva todos os itens de calendário no formato ICS. Os arquivos ICS podem então ser usados em qualquer outro programa que possa carregar o arquivo de calendário ICS padrão. Aberto no Microsoft Outlook, um arquivo ICS se parece com o da captura de tela abaixo.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
O seguinte snippet de código mostra como exportar os itens de calendário do PST do Outlook para o formato ICS.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveCalendarItems-SaveCalendarItems.cpp" >}}