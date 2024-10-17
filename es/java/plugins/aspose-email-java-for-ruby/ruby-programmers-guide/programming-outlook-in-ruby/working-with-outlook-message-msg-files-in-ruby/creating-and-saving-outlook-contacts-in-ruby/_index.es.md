---
title: "Creación y guardado de contactos de Outlook en Ruby"
url: /es/java/creando-y-guardando-contactos-de-outlook-en-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Creando y guardando contactos de Outlook**
Para crear contactos de Outlook utilizando **Aspose.Email Java para Ruby**, simplemente invoque el módulo **CreateOutlookContact**. Aquí puede ver un código de ejemplo.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

contact = Rjb::import('com.aspose.email.MapiContact').new

\# Establecer diferentes propiedades de este ítem de contacto.

\# Establecer las propiedades del nombre usando MapiContactNamePropertySet

name_prop_set = Rjb::import('com.aspose.email.MapiContactNamePropertySet').new

name_prop_set.setSurname("Mellissa")

name_prop_set.setGivenName("MacBeth")

contact.setNameInfo(name_prop_set)

\# Establecer propiedades profesionales usando MapiContactProfessionalPropertySet

prof_prop_set = Rjb::import('com.aspose.email.MapiContactProfessionalPropertySet').new

prof_prop_set.setTitle("Representante de cuentas")

prof_prop_set.setCompanyName("Contoso Ltd.")

prof_prop_set.setOfficeLocation("36/2529")

contact.setProfessionalInfo(prof_prop_set)

\# Teléfonos

telephone = Rjb::import('com.aspose.email.MapiContactTelephonePropertySet').new

telephone.setAssistantTelephoneNumber("(831) 758-7214")

telephone.setBusiness2TelephoneNumber("(831) 759-2518")

telephone.setBusinessTelephoneNumber("(831) 758-7285")

telephone.setCallbackTelephoneNumber("(831) 758-7321 (Después del horario")

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

\# Establecer la dirección física usando MapiContactPhysicalAddress y MapiContactPhysicalAddressPropertySet

phys_addrss = Rjb::import('com.aspose.email.MapiContactPhysicalAddress').new

phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

phys_addr_prop_set = Rjb::import('com.aspose.email.MapiContactPhysicalAddressPropertySet').new

phys_addr_prop_set.setWorkAddress(phys_addrss)

contact.setPhysicalAddresses(phys_addr_prop_set)

\# Establecer la información de email usando MapiContactElectronicAddress y MapiContactElectronicAddressPropertySet

email = Rjb::import('com.aspose.email.MapiContactElectronicAddress').new

email.setAddressType("SMTP")

email.setDisplayName("Melissa MacBeth (mellissa@contoso.com)")

email.setEmailAddress("melissa@contoso.com")

elec_addr_prop_set = Rjb::import('com.aspose.email.MapiContactElectronicAddressPropertySet').new

elec_addr_prop_set.setEmail1(email)

contact.setElectronicAddresses(elec_addr_prop_set)

contact.save(data_dir + "OutlookContact.vcf", Rjb::import('com.aspose.email.ContactSaveFormat').VCard)

puts "Contacto de Outlook creado con éxito."

```
## **Código en ejecución para descarga**
Descargue **Creación y guardado de contactos de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlookcontact.rb)