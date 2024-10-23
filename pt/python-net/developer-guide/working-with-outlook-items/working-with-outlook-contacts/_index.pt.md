---
title: "Trabalhando com Contatos do Outlook"
url: /pt/python-net/trabalhando-com-contatos-do-outlook/
weight: 90
type: docs
---


## **Criando, Salvando e Lendo Contatos**
Assim como o MapiMessage, o Aspose.Email permite que você crie contatos do Outlook. A classe MapiContact fornece todas as propriedades relacionadas a contatos necessárias para criar um contato do Outlook. Este artigo mostra como criar, salvar e ler um contato do Outlook usando a classe MapiContact.
### **Criar e Salvar Contato do Outlook**
Para criar um contato e salvá-lo no disco:

1. Instancie um novo objeto da classe MapiContact.
1. Insira as informações das propriedades do contato.
1. Adicione dados de foto (se houver).
1. Salve o contato no formato MSG ou VCard.

O seguinte trecho de código mostra como criar e salvar um contato do Outlook.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
contact.professional_info = ae.mapi.MapiContactProfessionalPropertySet("Awthentikz", "Assistente de trabalho social")
contact.personal_info.personal_home_page = "B2BTies.com"
contact.physical_addresses.work_address.address = "Im Astenfeld 59 8580 EDELSCHROTT"
contact.electronic_addresses.email1 = ae.mapi.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com")
contact.telephones = ae.mapi.MapiContactTelephonePropertySet("06605045265")
contact.personal_info.children = ["child1", "child2", "child3"]
contact.categories = ["category1", "category2", "category3"]
contact.mileage = "Alguma quilometragem de teste"
contact.billing = "Informações de cobrança de teste"
contact.other_fields.journal = True
contact.other_fields.private = True
contact.other_fields.reminder_topic = "Tópico de teste"
contact.other_fields.user_field1 = "CampoUsuarioContato1"
contact.other_fields.user_field2 = "CampoUsuarioContato2"
contact.other_fields.user_field3 = "CampoUsuarioContato3"
contact.other_fields.user_field4 = "CampoUsuarioContato4"

# Adicionar uma foto
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Salvar o Contato no formato MSG
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Salvar o Contato no formato VCF
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Salvar Contato no Formato VCF Versão 3**

Para salvar um contato no formato VCF Versão 3, use a propriedade *version* da classe [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). Crie uma nova instância da classe VCardSaveOptions, defina a propriedade de versão do objeto VCardSaveOptions para VCardVersion.V30. Isso define a versão do vCard para 3.0., chame o método *save* do objeto MapiContact, passando o nome do arquivo "contact.vcf" e o objeto VCardSaveOptions como parâmetros. Isso salva o contato como um arquivo vCard com o nome de arquivo e opções especificados. O seguinte trecho de código mostra como salvar um contato no formato VCF Versão 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Lendo um MapiContact**
A classe MapiContact pode ser usada para carregar contatos do formato Outlook MSG e VCard. O seguinte trecho de código mostra como carregar contatos do Outlook salvos como MSG e VCF em um MapiContact.
#### **Carregando um Contato do MSG**
O seguinte trecho de código mostra como carregar um contato do MSG.




{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Carregando um Contato do VCard**
O seguinte trecho de código mostra como carregar um contato do vCard.




{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Carregando um Contato do VCard com Codificação Especificada**
O seguinte trecho de código mostra como carregar um contato do vCard com codificação especificada.




{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Salvando Itens de Contato VCard com Codificação Especificada**

Ao salvar um arquivo vCard, é possível especificar a codificação de caracteres a ser usada, garantindo compatibilidade com caracteres não ASCII. Defina a propriedade *preferred_text_encoding* do objeto VCardSaveOptions para "utf-8". O seguinte trecho de código mostra como implementar esta função em seu projeto:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Salvando Arquivos VCard com Campos Estendidos**

Ao salvar um arquivo vCard, você também pode especificar opções, incluindo o uso de campos estendidos, que são propriedades ou atributos adicionais que podem ser adicionados a um vCard além do conjunto padrão de campos definidos pela especificação vCard. A propriedade *use_extensions* da classe [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) permite que você faça isso. O seguinte trecho de código mostra como salvar um arquivo VCard com campos estendidos:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Lendo Múltiplos Contatos no Formato VCard**

Você precisará dos seguintes métodos para obter a lista de todos os contatos de um VCard:

```
# Verifica se o fluxo de origem VCard contém múltiplos contatos.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Carrega a lista de todos os contatos do arquivo VCard.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Carrega a lista de todos os contatos do fluxo VCard.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
O trecho de código abaixo demonstrará o processo de leitura de múltiplos contatos de um arquivo VCard:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)

if ae.personalinfo.vcard.VCardContact.is_multi_contacts("contact.vcf"):
    ae.personalinfo.vcard.VCardContact.load_as_multiple("contact.vcf")
```

## **Renderizando Informações de Contato para MHTML**
O Contato do Outlook pode ser convertido para MHTML usando a API Aspose.Email. Este exemplo mostra como um VCard é carregado em um MapiContact e depois convertido para MHTML com a ajuda da API MailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}