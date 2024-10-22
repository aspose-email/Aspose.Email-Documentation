---
title: "Creando y Guardando Contactos de Outlook en Python"
url: /es/java/creando-y-guardando-contactos-de-outlook-en-python/
weight: 10
type: docs
---

## **Aspose.Email - Creando y Guardando Contactos de Outlook**
Para crear y guardar contactos de Outlook usando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código Python**

```python



contact = self.MapiContact()

\# Establecer diferentes propiedades de este elemento de contacto.

\# Establecer propiedades de nombre usando MapiContactNamePropertySet

name_prop_set = self.MapiContactNamePropertySet()

name_prop_set.setSurname("Mellissa")

name_prop_set.setGivenName("MacBeth")

contact.setNameInfo(name_prop_set)

\# Establecer propiedades profesionales usando MapiContactProfessionalPropertySet

prof_prop_set = self.MapiContactProfessionalPropertySet()

prof_prop_set.setTitle("Representante de Cuenta")

prof_prop_set.setCompanyName("Contoso Ltd.")

prof_prop_set.setOfficeLocation("36/2529")

contact.setProfessionalInfo(prof_prop_set)

\# Teléfonos

telephone = self.MapiContactTelephonePropertySet()

telephone.setAssistantTelephoneNumber("(831) 758-7214")

telephone.setBusiness2TelephoneNumber("(831) 759-2518")

telephone.setBusinessTelephoneNumber("(831) 758-7285")

telephone.setCallbackTelephoneNumber("(831) 758-7321 (Fuera de horario)")

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

\# Establecer dirección física usando MapiContactPhysicalAddress y MapiContactPhysicalAddressPropertySet

phys_addrss = self.MapiContactPhysicalAddress()

phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

phys_addr_prop_set = self.MapiContactPhysicalAddressPropertySet()

phys_addr_prop_set.setWorkAddress(phys_addrss)

contact.setPhysicalAddresses(phys_addr_prop_set)

\# Establecer información de correo electrónico usando MapiContactElectronicAddress y MapiContactElectronicAddressPropertySet

email = self.MapiContactElectronicAddress()

email.setAddressType("SMTP")

email.setDisplayName("Melissa MacBeth (mellissa@contoso.com)")

email.setEmailAddress("melissa@contoso.com")

elec_addr_prop_set = self.MapiContactElectronicAddressPropertySet()

elec_addr_prop_set.setEmail1(email)

contact.setElectronicAddresses(elec_addr_prop_set)

contactSaveFormat = self.ContactSaveFormat

contact.save(self.dataDir + "OutlookContact.vcf", contactSaveFormat.VCard)

print "Contacto de Outlook creado exitosamente."

```
## **Descargar Código en Ejecución**
Descarga **Creando y Guardando Contactos de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)