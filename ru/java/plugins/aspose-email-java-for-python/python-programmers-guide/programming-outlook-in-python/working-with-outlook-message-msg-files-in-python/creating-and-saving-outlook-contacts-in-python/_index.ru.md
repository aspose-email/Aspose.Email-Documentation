---
title: "Создание и сохранение контактов Outlook в Python"
url: /ru/java/creating-and-saving-outlook-contacts-in-python/
weight: 10
type: docs
---

## **Aspose.Email - Создание и сохранение контактов Outlook**
Чтобы создать и сохранить контакты Outlook с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

```python



contact = self.MapiContact()

\# Установите различные свойства этого элемента контакта.

\# Установите свойства имени с помощью MapiContactNamePropertySet

name_prop_set = self.MapiContactNamePropertySet()

name_prop_set.setSurname("Мелисса")

name_prop_set.setGivenName("Макбет")

contact.setNameInfo(name_prop_set)

\# Установите профессиональные свойства с помощью MapiContactProfessionalPropertySet

prof_prop_set = self.MapiContactProfessionalPropertySet()

prof_prop_set.setTitle("Представитель по аккаунту")

prof_prop_set.setCompanyName("Contoso Ltd.")

prof_prop_set.setOfficeLocation("36/2529")

contact.setProfessionalInfo(prof_prop_set)

\# Телефоны

telephone = self.MapiContactTelephonePropertySet()

telephone.setAssistantTelephoneNumber("(831) 758-7214")

telephone.setBusiness2TelephoneNumber("(831) 759-2518")

telephone.setBusinessTelephoneNumber("(831) 758-7285")

telephone.setCallbackTelephoneNumber("(831) 758-7321 (После рабочего времени")

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

\# Установите физический адрес с использованием MapiContactPhysicalAddress и MapiContactPhysicalAddressPropertySet

phys_addrss = self.MapiContactPhysicalAddress()

phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

phys_addr_prop_set = self.MapiContactPhysicalAddressPropertySet()

phys_addr_prop_set.setWorkAddress(phys_addrss)

contact.setPhysicalAddresses(phys_addr_prop_set)

\# Установите информацию об электронной почте с использованием MapiContactElectronicAddress и MapiContactElectronicAddressPropertySet

email = self.MapiContactElectronicAddress()

email.setAddressType("SMTP")

email.setDisplayName("Мелисса Макбет (mellissa@contoso.com)")

email.setEmailAddress("melissa@contoso.com")

elec_addr_prop_set = self.MapiContactElectronicAddressPropertySet()

elec_addr_prop_set.setEmail1(email)

contact.setElectronicAddresses(elec_addr_prop_set)

contactSaveFormat = self.ContactSaveFormat

contact.save(self.dataDir + "OutlookContact.vcf", contactSaveFormat.VCard)

print "Контакт Outlook успешно создан."

```
## **Скачать рабочий код**
Скачайте **Создание и сохранение контактов Outlook (Aspose.Email)** с любого из ниже упомянутых сайтов для совместного кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)