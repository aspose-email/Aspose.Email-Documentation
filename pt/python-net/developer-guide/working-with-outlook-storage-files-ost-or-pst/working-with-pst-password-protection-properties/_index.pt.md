---
title: "Trabalhando com Propriedades de Proteção por Senha de PST"
url: /pt/python-net/trabalhando-com-propriedades-de-protecao-por-senha-de-pst/
weight: 110
type: docs
---


O Microsoft Outlook permite que os usuários protejam arquivos PST com senha para restringir o acesso a eles. Aspose.Email pode detectar a proteção por senha em um arquivo PST. Este artigo mostra como:

- Verificar a Proteção por Senha de um PST
- Ler Arquivos PST Protegidos por Senha
- Validar Senha em PST Protegido por Senha
- Adicionar/Mudar/Remover Senha em Arquivos PST
## **Verificar Proteção por Senha**

Para verificar se um arquivo PST está protegido por uma senha, use o método *is_password_protected* da classe [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"O armazenamento está protegido por senha - {pst.store.is_password_protected}")
```

## **Ler Arquivos PST Protegidos por Senha**

Você pode ler arquivos protegidos por senha da mesma maneira que arquivos PST não protegidos. O seguinte trecho de código permite que você acesse cada mensagem individual com a possibilidade de processamento adicional:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # faça algo
```
## **Validar Senha em PST Protegido por Senha**

Para verificar se uma senha em um arquivo PST é válida, a Aspose.Email fornece o método *is_password_valid(password)* da classe [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Ele aceita a senha em forma de string como parâmetro e retorna True se a senha estiver correta e False se estiver incorreta.

O seguinte trecho de código demonstra o uso do método *is_password_valid(password)*.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Senha é válida - {pst.store.is_password_valid('Password1')}")
```

## **Adicionar/Mudar/Remover Senha em Arquivos PST**

O método *change_password(password)* da classe [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) é usado para manipular senhas em arquivos PST. O seguinte exemplo de código mostra como adicionar, mudar ou remover uma senha:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Adicionar ou mudar a senha
password = "Password1"
pst.store.change_password(password)
# Remover a senha
pst.store.change_password(None)
```