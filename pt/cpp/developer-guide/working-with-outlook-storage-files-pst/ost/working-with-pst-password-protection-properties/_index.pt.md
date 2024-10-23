---
title: "Trabalhando com Propriedades de Proteção por Senha do PST"
url: /pt/cpp/trabalhando-com-propriedades-de-protecao-por-senha-do-pst/
weight: 110
type: docs
---

## **Trabalhando com Propriedades de Proteção por Senha do PST**
O Microsoft Outlook permite que os usuários protejam arquivos PST com senha para restringir o acesso a eles. Aspose.Email pode detectar a proteção por senha em um arquivo PST. Este artigo mostra como:

- Remover/Redefinir a propriedade de Senha do PST
- Definir/Alterar a Senha do PST
### **Removendo/Redefinindo a Propriedade PR_PST_PASSWORD**
A remoção da propriedade PR_PST_PASSWORD não pode ser realizada como outras propriedades são removidas de um armazenamento de mensagens. Em vez disso, precisamos definir seu valor como zero (0) para que ela seja removida. A propriedade "Store" da classe PST permite acessar as propriedades de armazenamento do PST em vez das MessageStoreProperties do PST neste caso. O seguinte trecho de código mostra como remover/redefinir a propriedade PR_PST_PASSWORD.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}
### **Definindo a Senha em Arquivos PST**
O seguinte trecho de código mostra como definir a senha em arquivos PST.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}