---
title: "Ler e Converter arquivo OST do Outlook"
url: /pt/cpp/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

## **Ler e Converter arquivo OST do Outlook**
Aspose.Email para C++ fornece uma API para leitura de arquivos OST do Microsoft Outlook. Você pode carregar um arquivo OST do disco ou fluxo em uma instância da classe Aspose.Email.Outlook.Pst.PersonalStorage e obter informações sobre seu conteúdo, como pastas, subpastas e mensagens. O Microsoft Outlook cria um arquivo PST para armazenar e-mails quando servidores de correio POP3 ou IMAP são usados para baixar mensagens. Ele cria um arquivo OST quando o Microsoft Exchange é o servidor de correio. OST suporta tamanhos de arquivo maiores do que arquivos PST.
### **Lendo arquivos OST**
O processo para ler um arquivo OST com Aspose.Email é exatamente o mesmo que para ler um arquivo PST. O mesmo código pode ler arquivos PST e OST: basta fornecer o nome correto do arquivo para o método PersonalStorage.FromFile(). O seguinte trecho de código mostra como ler arquivos OST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}
### **Convertendo OST para PST**
Aspose.Email torna possível converter um arquivo OST para PST com uma única linha de código. Da mesma forma, um arquivo OST pode ser criado a partir de um arquivo PST usando a mesma linha de código com o enumerador FileFormat. No momento, a API suporta a conversão de formatos OST para PST, exceto OST 2013/2016. O seguinte trecho de código mostra como converter OST para PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}