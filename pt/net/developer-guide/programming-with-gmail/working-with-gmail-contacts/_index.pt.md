---
title: "Trabalhando com Contatos do Gmail"
url: /pt/net/trabalhando-com-contatos-do-gmail/
weight: 30
type: docs
---


Aspose.Email suporta o trabalho com contatos do Gmail. Usando a interface [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), os usuários podem recuperar contatos de uma conta do Gmail, criar novos contatos e atualizar e excluir contatos existentes. O Gmail permite que os desenvolvedores realizem todas essas operações usando sua API pública para desenvolvedores. As seguintes informações do usuário são necessárias para trabalhar com contatos do Gmail:
Nome de usuário, endereço de e-mail, senha, ID do cliente, token secreto de atualização do cliente.
Este artigo mostra como:

- [Acessar contatos do Gmail](/email/net/trabalhando-com-contatos-do-gmail/).
- [Criar novos contatos do Gmail](/email/net/trabalhando-com-contatos-do-gmail/).
- [Atualizar contatos existentes](/email/net/trabalhando-com-contatos-do-gmail/).
- [Excluir um contato](/email/net/trabalhando-com-contatos-do-gmail/).
- [Salvar contato](/email/net/trabalhando-com-contatos-do-gmail/).
  
## **Acessar Contatos do Gmail**

O seguinte é um aplicativo de exemplo que pode ser usado para acessar os detalhes dos contatos em todos os grupos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Criando Contato**

O seguinte trecho de código mostra como criar um contato.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Atualizando Contato**

Uma vez que um contato é recuperado, seus atributos podem ser atualizados e o contato pode ser salvo de volta na conta do Gmail. O seguinte trecho de código mostra como recuperar contatos de uma conta do Gmail e, em seguida, modificar um deles que é salvo novamente.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Excluindo Contato**

Para excluir um contato do Gmail, o método [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method) do cliente Gmail é usado, conforme mostrado no seguinte trecho de exemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Salvando Contato**

Aspose.Email permite salvar contatos em vários formatos de saída, como MSG e VCF. O método [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) fornece a capacidade de atingir isso. O seguinte trecho de código mostra como salvar um contato.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}