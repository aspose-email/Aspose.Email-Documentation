---
title: "Работа с параметрами защиты паролем PST"
url: /ru/python-net/working-with-pst-password-protection-properties/
weight: 110
type: docs
---


Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем на файле PST. В этой статье показано, как:

- Проверить наличие защиты паролем у PST
- Читать файлы PST с защитой паролем
- Проверить правильность пароля в защищенном паролем PST
- Добавить/изменить/удалить пароль в файлах PST
## **Проверка защиты паролем**

Чтобы проверить, защищен ли файл PST паролем, используйте метод *is_password_protected* класса [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class), как показано в примере кода ниже: 

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Хранилище защищено паролем - {pst.store.is_password_protected}")
```

## **Чтение файлов PST с защитой паролем**

Вы можете читать файлы с защитой паролем так же, как и обычные файлы PST без защиты. Следующий фрагмент кода позволяет получить доступ к каждому отдельному сообщению с возможностью его дальнейшей обработки:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # что-то сделать
```
## **Проверка пароля в защищенном паролем PST**

Чтобы проверить, является ли пароль в файле PST действительным, Aspose.Email предоставляет метод *is_password_valid(password)* класса [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Он принимает строку пароля в качестве параметра и возвращает True, если пароль правильный, и False, если он неверный.

Следующий фрагмент кода демонстрирует использование метода *is_password_valid(password)*.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Пароль действителен - {pst.store.is_password_valid('Password1')}")
```

## **Добавление/изменение/удаление пароля в файлах PST**

Метод *change_password(password)* класса [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) используется для работы с паролями в файлах PST. Следующий пример кода показывает, как добавить, изменить или удалить пароль:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Добавить или изменить пароль
password = "Password1"
pst.store.change_password(password)
# Удалить пароль
pst.store.change_password(None)
```