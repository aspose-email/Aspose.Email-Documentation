---
title: "Trabalhando com Contatos do Outlook"
url: /pt/java/trabalhando-com-contatos-do-outlook/
weight: 80
type: docs
---

## **Criar Contato do Outlook**

Aspose.Email para Java suporta a criação de contatos do Outlook (VCards) usando a classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/). [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) contém muitos métodos, alguns dos quais são listados abaixo.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) contém um conjunto de [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) contém um conjunto de [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)

### **Estrutura de Contato em Aspose.Email para Java**

Abaixo está a hierarquia implementada para contatos em Aspose.Email para Java. O nome da classe relevante é fornecido contra cada propriedade. Hiperligações são fornecidas para a documentação online para referência adicional.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Endereços Eletrônicos](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Tipo de Endereço
         1. Nome para Exibição
         1. Endereço de Email
         1. Número de Fax
      1. Email2
      1. Email3
      1. Fax Residencial
      1. Fax Primário
      1. Fax Comercial
   1. [Eventos](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (`MapiContactEventPropertySet`). Veja abaixo um exemplo de como definir eventos.
      1. Aniversário
      1. Aniversário de Casamento
   1. [Informações do Nome](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (`MapiContactNamePropertySet`)
      1. Nome para Exibição
      1. Prefixo do Nome para Exibição
      1. Arquivar Sob
      1. Arquivar Sob ID
      1. Geração
      1. Nome Dado
      1. Iniciais
      1. Nome do Meio
      1. Apelido
      1. Sobrenome
   1. [Informações Pessoais](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Conta
      1. Página Inicial Comercial
      1. Nome da Rede do Computador
      1. ID do Cliente
      1. Localização Comercial Gratuita
      1. Site FTP
      1. Gênero
      1. Número de Identificação do Governo
      1. Hobbies
      1. HTML
      1. Endereço de Mensagens Instantâneas
      1. Idioma
      1. Localização
      1. Notas
      1. Número de Identificação Organizacional
      1. Página Inicial Pessoal
      1. Referido por Nome
      1. Nome do Cônjuge
   1. [Endereço Físico](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Endereço Residencial](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Endereço
         1. Cidade
         1. País
         1. Código do País
         1. Código Postal
         1. Caixa Postal
         1. Estado ou Província
      1. Outro Endereço
      1. Endereço de Trabalho
   2. [Informações Profissionais](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Assistente
      2. Nome da Empresa
      3. Nome do Departamento
      4. Nome do Gerente
      5. Localização do Escritório
      6. Profissão
      7. Título
   3. [Telefones](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Número de Telefone do Assistente
      2. Número de Telefone Comercial 2
      3. Número de Telefone Comercial
      4. Número de Telefone de Retorno
      5. Número de Telefone do Carro
      6. Número de Telefone Principal da Empresa
      7. Número de Telefone Residencial 2
      8. Número de Telefone Residencial
      9. Número ISDN
      10. Número de Telefone Celular
      11. Outro Número de Telefone
      12. Número de Telefone do Pager
      13. Número de Telefone Primário
      14. Número de Telefone de Rádio
      15. Número de Telex
      16. Número de Telefone TTY/TDD

O seguinte código usa Aspose.Email para criar um contato do Outlook e preenchê-lo com nome, propriedades profissionais, endereço físico e email. Também mostra como adicionar [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) ao contato.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
| :- |
|**Figura: Um contato do Microsoft Outlook codificado com Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Adicionando Informações de Evento ao MapiContact**

O Microsoft Outlook permite que os usuários adicionem informações de evento a um contato. O evento contém o aniversário e o aniversário de casamento. Aspose.Email fornece a classe [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) para adicionar essas informações a um contato. Isso é detalhado no seguinte exemplo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Criando, Salvando e Lendo Contatos do Outlook**

Aspose.Email permite que desenvolvedores criem contatos do Microsoft Outlook, bem como mensagens de email. A classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) fornece todas as propriedades de contato necessárias para criar um contato do Outlook. Este artigo mostra como criar, salvar e ler um contato do Outlook usando a classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

### **Criar e Salvar um MapiContact**

Os seguintes passos podem ser usados para criar e salvar um contato no disco:

1. Instanciar um novo objeto da classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Inserir informações relacionadas a várias propriedades do contato.
1. Adicionar dados de foto ao contato, se houver.
1. Salvar o contato no formato MSG ou VCard.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Salvar Contato no Formato VCF da Versão 3**

Para salvar o contato no formato VCF da versão 3, use o [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerável para definir a propriedade [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--). O seguinte código de exemplo demonstra o uso do [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerável para salvar o contato no formato VCF da versão 3.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Ler um MapiContact**

A classe [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) pode ser usada para carregar arquivos MSG do Microsoft Outlook, assim como contatos no formato VCard. Os seguintes exemplos de código mostram como carregar contatos do Outlook salvos como MSG e VCF no [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Carregar um Contato de MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Carregar um Contato de VCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Carregar Contato VCard com Codificação Especificada**

Método Suportado: [MapiContact.fromVCard(String, Encoding)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Renderizando Informações de Contato para MHTML**

O Contato do Outlook pode ser convertido para MHTML usando a API Aspose.Email. Este exemplo mostra como um VCard é carregado no [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) e então convertido para MHTML com a ajuda da API [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}