---
title: "Работа со свойствами защиты паролем PST"
url: /ru/cpp/working-with-pst-password-protection-properties/
weight: 110
type: docs
---

## **Работа со свойствами защиты паролем PST**
Microsoft Outlook позволяет пользователям защищать PST-файлы паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем в PST-файле. В этой статье показано, как:

- Удалить/сбросить свойство Password из PST
- Установка/изменение пароля PST
### **Удаление/сброс свойства PR_PST_PASSWORD**
Невозможно удалить свойство PR_PST_PASSWORD, так как другие свойства удаляются из хранилища сообщений. Вместо этого нам нужно присвоить этому значению ноль (0), чтобы удалить его. Свойство «Store» класса PST в данном случае позволяет обращаться к свойствам хранилища PST вместо MessageStoreProperties из PST. В следующем фрагменте кода показано, как удалить/сбросить свойство PR_PST_PASSWORD.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}
### **Настройка пароля для файлов PST**
В следующем фрагменте кода показано, как установить пароль для файлов PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}
