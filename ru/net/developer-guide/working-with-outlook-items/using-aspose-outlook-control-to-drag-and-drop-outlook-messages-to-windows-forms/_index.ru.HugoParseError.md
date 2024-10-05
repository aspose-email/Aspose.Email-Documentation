---
title: Использование управления Aspose Outlook для перетаскивания и сброса сообщений Outlook в Windows Forms
type: docs
weight: 45
url: /net/using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms/
---


Aspose.Email поддерживает функцию перетаскивания и сброса в Microsoft Outlook. Это позволяет разработчикам легко создавать элементы пользовательского интерфейса, которые реагируют на события перетаскивания и сброса Outlook. В следующем примере показано, как создать панель, на которую пользователи могут перетаскивать сообщение из Outlook и сбрасывать его, а также программу для сохранения сообщений в файлы MSG. Следующий фрагмент кода показывает, как настроить управление Aspose Outlook, которое может принимать сброшенные сообщения Microsoft Outlook.

- Создайте приложение Windows Forms.
- Добавьте ссылку на сборку Aspose.Email.
- Перейдите к Aspose.Email.dll и нажмите **OK**.

Элемент пользовательского интерфейса, созданный в этом примере, — это панель. Чтобы создать панель:

- Щелкните правой кнопкой мыши на вашем проекте в панели решений и выберите **Добавить**, затем **Новый элемент** в меню.
- Создайте класс под названием MyPanel:
- Пусть MyPanel будет подклассом System.Windows.Form.Panel и добавьте свойство Aspose.Email.Windows.Forms.FileDropTargetManager в MyPanel:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-FileDropTargetManager.cs" >}}

- Переопределите методы OnHandleCreated и OnHandleDestroyed для регистрации MyPanel с использованием Aspose.Email.Windows.Forms.FileDropTargetManager:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-OnHandleCreatedOnHandleDestroyed.cs" >}}

- Соберите проект.

MyPanel готов к использованию. Эта панель принимает события перетаскивания и сброса из Outlook.

- Откройте панель инструментов и перетащите MyPanel на вашу форму Windows:

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_1.png)|
| :- |

- Добавьте обработчик событий для события DragDrop MyPanel. (Не забудьте установить свойство AllowDrop в true на панели свойств и изменить свойство BackColor MyPanel на ваше любимое.)

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_2.png)|
| :- |

- Добавьте следующую строку в метод InitializeComponent() основной формы:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages.Designer-AllowDrop.cs" >}}

- Реализуйте обработчик события DragDrop для сохранения сообщений, перетащенных из Outlook, в файлы MSG.
- Преобразуйте DragEventArgs в Aspose.Email.Windows.Forms.FileDragEventArgs, который содержит массив свойства Files, представляющий целевой объект перетаскивания пользователя.

Если пользователь перетаскивает несколько сообщений из Outlook и сбрасывает их на MyPanel, Files.Count — это количество сообщений, а Files итерируется для каждого сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages-DisplayFilesCount.cs" >}}

- Запустите проект и протестируйте его.

Теперь вы можете перетаскивать сообщения из Outlook и сбрасывать их в ваше приложение. Приложение предложит вам сохранить эти сообщения в файлы MSG.