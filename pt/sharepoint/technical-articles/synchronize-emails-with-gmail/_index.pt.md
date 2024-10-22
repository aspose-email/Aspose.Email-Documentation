---
title: "Sincronizar E-mails com Gmail"
url: /pt/sharepoint/synchronize-emails-with-gmail/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Aspose.Email para SharePoint suporta tanto os protocolos POP3 quanto IMAP ao sincronizar e-mails. O Gmail também permite acesso gratuito via POP e IMAP a clientes de e-mail como Outlook Express, Microsoft Office Outlook, Thunderbird ou qualquer API como Aspose.Network. 

Este artigo mostra como usar o recurso de sincronização de e-mails do Aspose.Email para SharePoint para sincronizar e-mails com o Gmail.

{{% /alert %}} 
## **Sincronizando E-mails**
O componente de conversão de e-mails do Aspose.Email para SharePoint é uma ferramenta fácil de usar para sincronizar e-mails com a lista personalizada de e-mails do SharePoint. Com suporte a protocolos e servidores de e-mail populares, como POP3, IMAP e Microsoft Exchange Server, o Aspose.Email pode se conectar a uma variedade de servidores de e-mail e sincronizar e-mails. 

Este artigo explica como [configurar o Gmail](/email/sharepoint/synchronize-emails-with-gmail/) para que os e-mails possam ser baixados, [configurar o SharePoint](/email/sharepoint/synchronize-emails-with-gmail/) para sincronizar e-mails e como [executar a sincronização manualmente](/email/sharepoint/synchronize-emails-with-gmail/).
### **Configurando o Gmail**
Para receber e-mails do Gmail usando um cliente de e-mail, o POP ou IMAP deve ser ativado na página de configurações do Gmail. Por padrão, está desativado.

Para ativar POP3 e IMAP:

1. Faça login na sua conta do Gmail e clique em **Configurações** no canto superior direito.
1. Clique em **Encaminhamento e POP/IMAP** para alterar as configurações de POP e IMAP.
1. Ative o POP e escolha a opção “Ativar POP” apropriada: 
   1. **Ativar POP para todos os e-mails** para baixar todos os e-mails (novos e antigos).
   1. **Ativar POP para e-mails que chegarem a partir de agora** para baixar apenas e-mails novos.
1. Ative o IMAP. Para IMAP, há apenas duas escolhas: 
   1. **Ativar** para baixar todas as mensagens da sua caixa de entrada.
   1. **Desativar** desativa o serviço. Não selecione esta opção. 

      **A guia Encaminhamento e POP/IMAP no Gmail** 

![todo:image_alt_text](synchronize-emails-with-gmail_1.png)

### **Configurando Aspose.Email para SharePoint**
1. No SharePoint, clique em **Configurações de Sincronização** na faixa de opções **Aspose Tools** para abrir a janela de configurações.
1. Especifique as configurações POP3 do Gmail para sincronizar com o Gmail usando o protocolo POP3. Insira as seguintes informações nesta tela: 
   1. Habilitar Sincronização: marcar
   1. Protocolo: POP3
   1. Servidor de e-mail: pop.gmail.com
   1. Porta: 995
   1. SSL: marcar
   1. Manter no Servidor: marcar
   1. Nome de usuário: username@gmail.com (especifique o endereço de e-mail completo)
   1. Senha: especifique a senha do Gmail
   1. Agendar: escolha “Minuto a minuto” e “A cada 5 minutos” ou o que for mais conveniente 
      **A caixa de diálogo Configurações de Sincronização.** 

![todo:image_alt_text](synchronize-emails-with-gmail_2.png)

1. Verifique a conexão clicando em **Clique para testar os parâmetros de conexão**. Se houver algo errado com as credenciais ou endereço do host, uma mensagem de erro será exibida.
1. Clique em **Salvar** para salvar as configurações. Aspose.Email para SharePoint tenta se conectar ao Gmail a cada 5 minutos (ou qualquer outro tempo especificado). Ele baixa mensagens e atualiza a lista de e-mails.

Todos os anexos, imagens incorporadas e formatação de corpo são preservados ao baixar as mensagens e criar e-mails na lista personalizada de e-mails do SharePoint. 
### **Sincronizando E-mails Manualmente**
Para iniciar a sincronização manualmente: 

1. Clique em **Sincronizar agora** na faixa de opções **Aspose Tools**. A caixa de diálogo Sincronizar Agora é exibida. A tela Sincronizar Agora mostra um resumo das configurações da conta de e-mail e o status da última sincronização. 

   **A caixa de diálogo Sincronizar Agora.** 

![todo:image_alt_text](synchronize-emails-with-gmail_3.png)

1. Clique em **Sincronizar Agora**. 

   **E-mails listados em uma lista do SharePoint após a sincronização bem-sucedida** 

![todo:image_alt_text](synchronize-emails-with-gmail_4.png)

1. Clique em qualquer e-mail da lista para abri-lo no SharePoint.

   **Um e-mail exibido no SharePoint.** 

![todo:image_alt_text](synchronize-emails-with-gmail_5.png)
## **Referências**
- [Instalando Aspose.Email para SharePoint](/email/sharepoint/install-aspose-email-for-sharepoint/)
- [Sincronizar E-mails com Servidor de E-mail](/email/sharepoint/email-synchronization/)
- [Sobre o Componente de Sincronização de E-mails para SharePoint](/email/sharepoint/about-email-synchronization/)