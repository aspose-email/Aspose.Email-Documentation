---
title: "Trabalhando com Propriedades de Proteção por Senha de PST"
url: /pt/net/trabalhando-com-propriedades-de-protecao-por-senha-de-pst/
weight: 100
type: docs
---

## **Trabalhando com Propriedades de Proteção por Senha de PST**

O Microsoft Outlook permite que os usuários protejam arquivos PST com uma senha para restringir o acesso a eles. Aspose.Email pode detectar a proteção por senha em um arquivo PST. A proteção por senha é, na verdade, implementada apenas no Outlook; os dados não são criptografados de forma alguma. E isso possibilita o uso da API para extrair e-mails sem saber a senha.

{{% alert %}}
**Experimente!**

Execute o projeto simples [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) e experimente os recursos do Aspose.Email para gerenciar senhas PST.
{{% /alert %}}

### **Ler Arquivos PST Protegidos por Senha**

Você pode ler arquivos protegidos por senha da mesma forma que arquivos PST não protegidos.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Verificar se o arquivo PST está Protegido por Senha**

A API fornece a propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/). A propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) retorna verdadeiro se o arquivo PST estiver protegido por senha e falso se não estiver.

O seguinte trecho de código demonstra o uso da propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"O armazenamento está protegido por senha - {pst.Store.IsPasswordProtected}");
```

## **Validar Senha em PST Protegido por Senha**

O método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) recebe a string senha como um parâmetro e retorna verdadeiro se a senha estiver correta e falso se estiver incorreta.

O seguinte trecho de código demonstra o uso do método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Senha é válida - {pst.Store.IsPasswordValid("Password1")}");
```

## **Adicionar/Alterar/Remover Senha em Arquivos PST**

O método [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) é utilizado para adicionar, alterar ou excluir uma senha.

Para fazer isso, siga estas etapas:

- Carregue o PST a partir de um arquivo ou de um fluxo.
- Chame o método [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/). Para adicionar ou alterar a senha, passe uma string de senha como parâmetro, e para remover a senha, passe um valor nulo.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Adicionar ou alterar a senha
const string password = "Password1";
pst.Store.ChangePassword(password);
// Remover a senha
pst.Store.ChangePassword(null);
```