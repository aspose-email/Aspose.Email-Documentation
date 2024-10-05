---
title: "Создание и сохранение контактов Outlook на Ruby"
url: /ru/java/creating-and-saving-outlook-contacts-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Создание и сохранение контактов Outlook**
Чтобы создать контакты Outlook с использованием **Aspose.Email Java для Ruby**, просто вызовите модуль **CreateOutlookContact**. Здесь вы можете видеть пример кода.

**Код Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

contact = Rjb::import('com.aspose.email.MapiContact').new

\# Установите различные свойства этого элемента контакта.

\# Установите свойства имени, используя MapiContactNamePropertySet

name_prop_set = Rjb::import('com.aspose.email.MapiContactNamePropertySet').new

name_prop_set.setSurname("Мелисса")

name_prop_set.setGivenName("Макбет")

contact.setNameInfo(name_prop_set)

\# Установите профессиональные свойства, используя MapiContactProfessionalPropertySet

prof_prop_set = Rjb::import('com.aspose.email.MapiContactProfessionalPropertySet').new

prof_prop_set.setTitle("Представитель по работе с клиентами")

prof_prop_set.setCompanyName("Contoso Ltd.")

prof_prop_set.setOfficeLocation("36/2529")

contact.setProfessionalInfo(prof_prop_set)

\# Телефоны

telephone = Rjb::import('com.aspose.email.MapiContactTelephonePropertySet').new

telephone.setAssistantTelephoneNumber("(831) 758-7214")

telephone.setBusiness2TelephoneNumber("(831) 759-2518")

telephone.setBusinessTelephoneNumber("(831) 758-7285")

telephone.setCallbackTelephoneNumber("(831) 758-7321 (после работы)")

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

phys_addrss = Rjb::import('com.aspose.email.MapiContactPhysicalAddress').new

phys_addrss.setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908")

phys_addr_prop_set = Rjb::import('com.aspose.email.MapiContactPhysicalAddressPropertySet').new

phys_addr_prop_set.setWorkAddress(phys_addrss)

contact.setPhysicalAddresses(phys_addr_prop_set)

\# Установите информацию об электронной почте, используя MapiContactElectronicAddress и MapiContactElectronicAddressPropertySet

email = Rjb::import('com.aspose.email.MapiContactElectronicAddress').new

email.setAddressType("SMTP")

email.setDisplayName("Мелисса Макбет (mellissa@contoso.com)")

email.setEmailAddress("melissa@contoso.com")

elec_addr_prop_set = Rjb::import('com.aspose.email.MapiContactElectronicAddressPropertySet').new

elec_addr_prop_set.setEmail1(email)

contact.setElectronicAddresses(elec_addr_prop_set)

contact.save(data_dir + "OutlookContact.vcf", Rjb::import('com.aspose.email.ContactSaveFormat').VCard)

puts "Контакт Outlook успешно создан."

```
## **Скачать работающий код**
Скачайте **Создание и сохранение контактов Outlook (Aspose.Email)** с любого из указанных ниже социальных кодирующих сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlookcontact.rb)