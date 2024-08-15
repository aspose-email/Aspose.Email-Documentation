---
title: "Работа со свойствами защиты паролем PST"
url: /ru/python-net/working-with-pst-password-protection-properties/
weight: 110
type: docs
---


Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем в PST-файле. В этой статье показано, как:

- Проверьте защиту PST паролем
- Чтение защищенных паролем файлов PST
- Подтвердите пароль в защищенном паролем PST
- Добавить/изменить/удалить пароль в файлах PST
## **Проверьте защиту паролем**

Чтобы проверить, защищен ли PST-файл паролем, используйте *is_password_protected* метод [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) класс, как показано в примере кода ниже:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"The storage is password protected - {pst.store.is_password_protected}")
```

## **Чтение защищенных паролем файлов PST**

Вы можете читать защищенные паролем файлы так же, как обычные незащищенные pst-файлы. Следующий фрагмент кода позволяет получить доступ к каждому отдельному сообщению с возможностью его дальнейшей обработки:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # do something
```
## **Подтвердите пароль в защищенном паролем PST**

Чтобы проверить, действителен ли пароль в файле PST, Aspose.Email предоставляет *is_password_valid(password)* метод [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) класс. Он принимает строковый пароль в качестве параметра и возвращает True, если пароль правильный, и False, если он неверен.

Следующий фрагмент кода демонстрирует использование *is_password_valid(password)* method.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Password is valid - {pst.store.is_password_valid('Password1')}")
```

## **Добавить/изменить/удалить пароль в файлах PST**

The *change_password(password)* метод [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) класс используется для управления паролями в файлах PST. В следующем примере кода показано, как добавить, изменить или удалить пароль:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Add or change the password
password = "Password1"
pst.store.change_password(password)
# Remove the password
pst.store.change_password(None)
```
