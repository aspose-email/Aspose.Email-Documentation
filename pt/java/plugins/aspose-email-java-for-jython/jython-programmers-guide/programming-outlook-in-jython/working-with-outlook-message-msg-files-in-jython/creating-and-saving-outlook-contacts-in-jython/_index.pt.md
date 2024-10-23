---
title: "Criando e Salvando Contatos do Outlook em Jython"
url: /pt/java/creating-and-saving-outlook-contacts-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Criando e Salvando Contatos do Outlook**
Para criar contatos do Outlook usando **Aspose.Email Java para Jython**, basta invocar o módulo **CreateOutlookContact**. Aqui você pode ver um código de exemplo.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiContact

from com.aspose.email import MapiContactNamePropertySet

from com.aspose.email import MapiContactProfessionalPropertySet

from com.aspose.email import MapiContactTelephonePropertySet

from com.aspose.email import MapiContactPhysicalAddress

from com.aspose.email import MapiContactPhysicalAddressPropertySet

from com.aspose.email import MapiContactElectronicAddress

from com.aspose.email import MapiContactElectronicAddressPropertySet

from com.aspose.email import ContactSaveFormat

class CreateOutlookContact:

    def __init__(self):

        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact/'

        contact = MapiContact()

        # Definir diferentes propriedades deste item de contato.

        # Definir propriedades de nome usando MapiContactNamePropertySet

        name_prop_set = MapiContactNamePropertySet()

        name_prop_set.setSurname("Mellissa")

        name_prop_set.setGivenName("MacBeth")

        contact.setNameInfo(name_prop_set)

        # Definir propriedades profissionais usando MapiContactProfessionalPropertySet

        prof_prop_set = MapiContactProfessionalPropertySet()

        prof_prop_set.setTitle("Representante de Conta")

        prof_prop_set.setCompanyName("Contoso Ltd.")

        prof_prop_set.setOfficeLocation("36/2529")

        contact.setProfessionalInfo(prof_prop_set)

        # Telefone

        telephone = MapiContactTelephonePropertySet()

        telephone.setAssistantTelephoneNumber("(831) 758-7214")

        telephone.setBusiness2TelephoneNumber("(831) 759-2518")

        telephone.setBusinessTelephoneNumber("(831) 758-7285")

        telephone.setCallbackTelephoneNumber("(831) 758-7321 (Após o expediente")

        telephone.setCarTelephoneNumber("(831) 758-7201")

        telephone.setCompanyMainTelephoneNumber("(831) 758-7368")

        telephone.setHome2TelephoneNumber("(831) 758-7256")

        telephone.setHomeTelephoneNumber("(831) 758-7257")

        telephone.setIsdnNumber("(831) 758-7381")

        telephone.setMobileTelephoneNumber("(831) 758-7368")

        telephone.setOtherTelephoneNumber("(831) 758-7201")

        telephone.setPagerTelephoneNumber("(831) 758-7368")

        telephone.setPrimaryTelephoneNumber("(831) 758-7334")

        telephone.setRadioTelephoneNumber("(831) 758-7234")

        telephone.setTelexNumber("(831) 758-7408")

        telephone.setTtyTddPhoneNumber("(800) 806-4474")

        contact.setTelephones(telephone)

        # Definir endereço físico usando MapiContactPhysicalAddress e MapiContactPhysicalAddressPropertySet

        phys_addrss = MapiContactPhysicalAddress()

        phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

        phys_addr_prop_set = MapiContactPhysicalAddressPropertySet()

        phys_addr_prop_set.setWorkAddress(phys_addrss)

        contact.setPhysicalAddresses(phys_addr_prop_set)

        # Definir informações de email usando MapiContactElectronicAddress e MapiContactElectronicAddressPropertySet

        email = MapiContactElectronicAddress()

        email.setAddressType("SMTP")

        email.setDisplayName("Melissa MacBeth (mellissa@contoso.com)")

        email.setEmailAddress("melissa@contoso.com")

        elec_addr_prop_set = MapiContactElectronicAddressPropertySet()

        elec_addr_prop_set.setEmail1(email)

        contact.setElectronicAddresses(elec_addr_prop_set)

        contactSaveFormat=ContactSaveFormat

        contact.save(dataDir + "OutlookContact.vcf", contactSaveFormat.VCard)

        print "Contato do Outlook criado com sucesso."

if __name__ == '__main__':        

    CreateOutlookContact()

```
## **Baixar Código em Execução**
Baixe **Criando e Salvando Contatos do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)