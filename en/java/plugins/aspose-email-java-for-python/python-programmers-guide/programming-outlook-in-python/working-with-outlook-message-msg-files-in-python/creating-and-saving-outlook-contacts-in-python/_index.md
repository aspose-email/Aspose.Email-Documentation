---
title: Creating and Saving Outlook Contacts in Python
type: docs
weight: 10
url: /java/creating-and-saving-outlook-contacts-in-python/
---

## **Aspose.Email - Creating and Saving Outlook Contacts**
To Create and Save Outlook Contacts using **Aspose.Email Java for Python**, Use following code.

**Python Code**

```python



contact = self.MapiContact()

\# Set different properties of this Contact Item.

\# Set Name properties using MapiContactNamePropertySet

name_prop_set = self.MapiContactNamePropertySet()

name_prop_set.setSurname("Mellissa")

name_prop_set.setGivenName("MacBeth")

contact.setNameInfo(name_prop_set)

\# Set professional properties using MapiContactProfessionalPropertySet

prof_prop_set = self.MapiContactProfessionalPropertySet()

prof_prop_set.setTitle("Account Representative")

prof_prop_set.setCompanyName("Contoso Ltd.")

prof_prop_set.setOfficeLocation("36/2529")

contact.setProfessionalInfo(prof_prop_set)

\# Telephones

telephone = self.MapiContactTelephonePropertySet()

telephone.setAssistantTelephoneNumber("(831) 758-7214")

telephone.setBusiness2TelephoneNumber("(831) 759-2518")

telephone.setBusinessTelephoneNumber("(831) 758-7285")

telephone.setCallbackTelephoneNumber("(831) 758-7321 (After hours")

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

\# Set Physical Address using MapiContactPhysicalAddress and MapiContactPhysicalAddressPropertySet

phys_addrss = self.MapiContactPhysicalAddress()

phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

phys_addr_prop_set = self.MapiContactPhysicalAddressPropertySet()

phys_addr_prop_set.setWorkAddress(phys_addrss)

contact.setPhysicalAddresses(phys_addr_prop_set)

\# Set email information using MapiContactElectronicAddress and MapiContactElectronicAddressPropertySet

email = self.MapiContactElectronicAddress()

email.setAddressType("SMTP")

email.setDisplayName("Melissa MacBeth (mellissa@contoso.com)")

email.setEmailAddress("melissa@contoso.com")

elec_addr_prop_set = self.MapiContactElectronicAddressPropertySet()

elec_addr_prop_set.setEmail1(email)

contact.setElectronicAddresses(elec_addr_prop_set)

contactSaveFormat = self.ContactSaveFormat

contact.save(self.dataDir + "OutlookContact.vcf", contactSaveFormat.VCard)

print "Created outlook contact successfully."

```
## **Download Running Code**
Download **Creating and Saving Outlook Contacts (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
