---
title: "Recursos de Utilitário do Microsoft Graph"
url: /pt/net/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Criando Projeto no Centro de Administração do Azure Active Directory**

Um projeto deve ser criado no centro de administração do Azure Active Directory para um usuário com conta do MS Office.

### **Passos para Criar um Projeto no Centro de Administração do Azure Active Directory**

Abaixo está um tutorial passo a passo para criar um projeto no centro de administração do Azure Active Directory.

#### 1. Vá para o Azure Active Directory e faça login usando suas credenciais do MS Office.

**Azure Active Directory** Link - <https://aad.portal.azure.com/>

#### 2. Crie um Aplicativo Azure AD em seu tenant.

No painel lateral esquerdo, clique no rótulo **Azure Active Directory**. Isso abrirá a blade do Azure Active Directory. Nessa tela, você deve ver um rótulo **App registrations**. Este é o ponto de partida para registrar um Aplicativo Azure AD. Esta blade permitirá que você crie um novo aplicativo para o Azure AD.

Clique no botão **Nova inscrição** para criar um novo aplicativo.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Agora você verá a blade de nova inscrição de aplicativo.

- **Nome** Este será o nome do seu aplicativo.
- **Tipos de conta suportados** Esta seção restringirá o acesso.

Clique no botão **Registrar**.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Você deve ver a blade de aplicativos recém-registrados.

- **ID do aplicativo (cliente)** O id do seu aplicativo.
- **ID do diretório (tenant)** O id do tenant do Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Permissões para a Microsoft Graph API.

Clique no rótulo **Permissões de API**.

O Azure já lhe concedeu permissões delegadas **User.Read** para seu aplicativo. Esta permissão nos permitirá ler as informações do usuário para um usuário logado. Essas são permissões da Microsoft Graph API, também podemos chamá-las de **Escopos**.

A lista completa de escopos para a Microsoft Graph API - <https://learn.microsoft.com/en-us/graph/permissions-reference>.

Clique no botão **+ Adicionar uma permissão** e selecione **Microsoft Graph**.

Clique em **Permissões delegadas**. Agora você verá uma lista de permissões disponíveis para a Microsoft Graph API.

Selecione as permissões necessárias e clique no botão **Adicionar permissões**.

Clique no botão **Conceder consentimento de administrador**.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Permitir fluxos de cliente público.

Especifica se o aplicativo é um cliente público. Apropriado para aplicativos que usam fluxos de concessão de token que não utilizam uma URI de redirecionamento.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Crie uma chave para o aplicativo.

![todo:image_alt_text](microsoft-graph-utility-features_5.png)