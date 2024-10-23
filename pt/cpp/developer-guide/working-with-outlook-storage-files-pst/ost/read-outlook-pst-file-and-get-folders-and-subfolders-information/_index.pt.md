---
title: "Ler arquivo PST do Outlook e obter informações sobre pastas e subpastas"
url: /pt/cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

## **Ler arquivo PST do Outlook e obter informações sobre pastas e subpastas**
Aspose.Email para C++ fornece uma API para ler arquivos PST do Microsoft Outlook. Você pode carregar um arquivo PST do disco ou stream para uma instância da classe PersonalStorage e obter informações sobre seu conteúdo, como pastas, subpastas e mensagens. A API também fornece a capacidade de incluir pastas de pesquisa enquanto percorre as mensagens das pastas PST.
### **Carregando um arquivo PST**
Um arquivo PST do Outlook pode ser carregado em uma instância da classe PersonalStorage. O seguinte trecho de código mostra como carregar o arquivo PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Exibindo informações de pastas**
Após carregar o arquivo PST na classe PersonalStorage, você pode obter informações sobre o nome de exibição do arquivo, pasta raiz, subpastas e contagem de mensagens. O seguinte trecho de código mostra como exibir o nome do arquivo PST, pastas e número de mensagens nas pastas.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Recuperando informações da pasta pai a partir de MessageInfo**
O seguinte trecho de código mostra como recuperar informações da pasta pai a partir de MessageInfo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}