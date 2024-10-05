---
title: "Функции утилиты Microsoft Graph"
url: /ru/net/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Создание проекта в Центре администрирования Azure Active Directory**

Проект должен быть создан в Центре администрирования Azure Active Directory для пользователя с учетной записью MS Office.

### **Шаги для создания проекта в Центре администрирования Azure Active Directory**

Ниже представлен пошаговый учебник по созданию проекта в Центре администрирования Azure Active Directory.

#### 1. Перейдите в Azure Active Directory и войдите, используя свои учетные данные MS Office.

**Azure Active Directory** Ссылка - <https://aad.portal.azure.com/>

#### 2. Создайте приложение Azure AD в вашем арендаторе.

В левой панели щелкните по ярлыку **Azure Active Directory**. Это откроет панель Azure Active Directory. На этом экране вы должны увидеть ярлык **Регистрация приложений**. Это стартовая точка для регистрации приложения Azure AD. Эта панель позволит вам создать новое приложение для Azure AD.

Нажмите кнопку **Новая регистрация**, чтобы создать новое приложение.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Теперь вы увидите панель регистрации нового приложения.

- **Имя** Это будет имя вашего приложения.
- **Поддерживаемые типы учетных записей** Этот раздел ограничит доступ.

Нажмите кнопку **Зарегистрировать**.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Вы должны увидеть панель недавно зарегистрированных приложений.

- **Идентификатор приложения (клиента)** Идентификатор вашего приложения.
- **Идентификатор директории (арендатора)** Идентификатор арендатора Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Предоставление разрешений для Microsoft Graph API.

Нажмите на ярлык **Разрешения API**.

Azure уже предоставил вашим приложением **User.Read** делегированные разрешения. Это разрешение позволит нам читать информацию о пользователе для вошедшего в систему пользователя. Это разрешения Microsoft Graph API, мы также можем называть их **Области**.

Полный список областей для Microsoft Graph API - <https://learn.microsoft.com/en-us/graph/permissions-reference>.

Нажмите кнопку **+ Добавить разрешение** и выберите **Microsoft Graph**.

Нажмите на **Делегированные разрешения**. Теперь вы видите список разрешений, доступных для Microsoft Graph API.

Выберите необходимые разрешения и нажмите кнопку **Добавить разрешения**.

Нажмите кнопку **Предоставить согласие администратора**.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Разрешить публичные клиентские потоки.

Указывает, является ли приложение публичным клиентом. Подходит для приложений, использующих потоки предоставления токенов, которые не используют URI перенаправления.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Создайте ключ для приложения.

![todo:image_alt_text](microsoft-graph-utility-features_5.png)