---
title: "Использование Aspose Outlook Control для перетаскивания сообщений Outlook в формы Windows"
url: /ru/net/using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms/
weight: 45
type: docs
---


Aspose.Email поддерживает функцию перетаскивания в Microsoft Outlook. Это позволяет разработчикам легко создавать элементы пользовательского интерфейса, реагирующие на события перетаскивания Outlook. В следующем примере показано, как создать панель, на которую пользователи могут перетаскивать сообщение из Outlook, а также программу для сохранения сообщений в MSG-файлы. В следующем фрагменте кода показано, как настроить элемент управления Aspose Outlook, который может принимать удаленные сообщения Microsoft Outlook.

- Создайте приложение для форм Windows.
- Добавьте ссылку на сборку Aspose.Email.
- Перейдите на страницу Aspose.email.dll и нажмите **OK**.

Элемент пользовательского интерфейса, созданный в этом примере, представляет собой панель. Чтобы создать панель, выполните следующие действия:

- Щелкните проект правой кнопкой мыши на панели решений и выберите **Add** а затем **Новый товар** из меню.
- Создайте класс под названием MyPanel:
- Позвольте MyPanel быть подклассом System.Windows.Form.Panel и добавьте свойство Aspose.Email.Windows.Forms.FileDropTargetManager в MyPanel:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-FileDropTargetManager.cs" >}}

- Переопределите методы onHandleCreated и onHandleDestroyed, чтобы зарегистрировать мою панель с помощью диспетчера Spose.email.Windows.forms.FileDropTargetManager:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-OnHandleCreatedOnHandleDestroyed.cs" >}}

- Создайте проект.

MyPanel готов к использованию. На этой панели можно перетаскивать события из Outlook.

- Откройте панель инструментов и перетащите MyPanel в форму Windows:

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_1.png)|
|: - |

- Добавьте обработчик событий в событие DragDrop в MyPanel. (Не забудьте задать свойству AllowDrop} значение true на панели свойств и изменить свойство myPanel backColor на свое любимое.)

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_2.png)|
|: - |

- Добавьте следующую строку в метод initializeComponent () основной формы:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages.Designer-AllowDrop.cs" >}}

- Реализуйте обработчик событий DragDrop для сохранения сообщений, перетаскиваемых из Outlook в файлы MSG.
- Преобразуйте значение dragEventArgs в объект Aspose.email.Windows.Forms.FileDragEventArgs, который содержит свойство массива Files, обозначающее цель перетаскивания пользователя.

Если пользователь перетаскивает несколько сообщений из Outlook и помещает их в MyPanel, Files.Count — это количество сообщений, а Files — это количество итераций для каждого сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages-DisplayFilesCount.cs" >}}

- Запустите проект и протестируйте его.

Теперь вы можете перетаскивать сообщения из Outlook в приложение. Приложение предложит вам сохранить эти сообщения в файлах MSG.
