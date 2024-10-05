---
title: Работа с свойствами защиты паролем PST
type: docs
weight: 110
url: /cpp/working-with-pst-password-protection-properties/
---

## **Работа с свойствами защиты паролем PST**
Microsoft Outlook позволяет пользователям защищать файлы PST паролем, чтобы ограничить к ним доступ. Aspose.Email может обнаружить защиту паролем в файле PST. В этой статье показано, как:

- Удалить/Сбросить свойство пароля из PST
- Установить/Изменить пароль PST
### **Удаление/Сброс свойства PR_PST_PASSWORD**
Удалить свойство PR_PST_PASSWORD невозможно так же, как удаляются другие свойства из хранилища сообщений. Вместо этого нам нужно установить его значение в ноль (0), чтобы оно было удалено. Свойство "Store" класса PST позволяет получить доступ к свойствам хранилища PST, вместо свойств MessageStoreProperties PST в этом случае. Следующий фрагмент кода показывает, как удалить/сбросить свойство PR_PST_PASSWORD.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}
### **Установка пароля для файлов PST**
Следующий фрагмент кода показывает, как установить пароль для файлов PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}