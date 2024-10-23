---
title: "Usando o Controle Aspose Outlook para Arrastar e Soltar Mensagens do Outlook em Windows Forms"
url: /pt/net/using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms/
weight: 45
type: docs
---


Aspose.Email suporta o recurso de arrastar e soltar do Microsoft Outlook. Isso permite que os desenvolvedores criem facilmente elementos de UI que respondem a eventos de arrastar e soltar do Outlook. O seguinte exemplo mostra como criar um painel no qual os usuários podem arrastar uma mensagem do Outlook e soltá-la, e o programa para salvar mensagens em arquivos MSG. O seguinte snippet de código mostra como configurar um controle Aspose Outlook que pode receber mensagens do Microsoft Outlook arrastadas.

- Crie um aplicativo de formulário do Windows.
- Adicione uma referência à biblioteca Aspose.Email.
- Navegue até o Aspose.Email.dll e clique em **OK**.

O elemento de UI criado neste exemplo é um painel. Para criar um painel:

- Clique com o botão direito do mouse em seu projeto no painel de solução e escolha **Adicionar** e depois **Novo item** no menu.
- Crie uma classe chamada MyPanel:
- Deixe MyPanel ser uma subclasse de System.Windows.Form.Panel, e adicione uma propriedade Aspose.Email.Windows.Forms.FileDropTargetManager a MyPanel:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-FileDropTargetManager.cs" >}}

- Substitua os métodos OnHandleCreated e OnHandleDestroyed para registrar MyPanel usando Aspose.Email.Windows.Forms.FileDropTargetManager:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-OnHandleCreatedOnHandleDestroyed.cs" >}}

- Compile o projeto.

MyPanel está pronto para uso. Este painel aceita eventos de arrastar e soltar do Outlook.

- Abra seu painel de ferramentas e arraste MyPanel para o seu formulário do Windows:

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_1.png)|
| :- |

- Adicione um manipulador de eventos ao evento DragDrop de MyPanel. (Não se esqueça de definir a propriedade AllowDrop como verdadeira no painel de propriedades e alterar a propriedade BackColor de MyPanel para a sua favorita.)

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_2.png)|
| :- |

- Adicione a seguinte linha no método InitializeComponent() do Form principal:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages.Designer-AllowDrop.cs" >}}

- Implemente o manipulador de eventos DragDrop para salvar as mensagens arrastadas do Outlook em arquivos MSG.
- Lance DragEventArgs para Aspose.Email.Windows.Forms.FileDragEventArgs, que contém uma propriedade de array Files que representa o alvo de arrastar do usuário.

Se um usuário arrastar várias mensagens do Outlook e soltá-las em MyPanel, Files.Count é o número de mensagens, e Files itera para cada mensagem.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages-DisplayFilesCount.cs" >}}

- Execute o projeto e teste-o.

Agora você pode arrastar mensagens do Outlook e soltá-las em sua aplicação. O aplicativo solicita que você salve essas mensagens em arquivos MSG.