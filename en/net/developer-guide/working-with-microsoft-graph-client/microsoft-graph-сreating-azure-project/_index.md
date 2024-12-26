---
title: Creating a Project in Azure Active Directory Admin Center
ArticleTitle: Creating a Project in Azure Active Directory Admin Center
type: docs
weight: 10
url: /net/microsoft-graph-сreating-azure-project/
---

A Project is to be created on Azure Active Directory admin center for a user having MS Office account.

### **Steps to Create a Project in Azure Active Directory Admin Center**

Below is a step by step tutorial for creating a project in Azure Active Directory admin center.

#### 1. Go to Azure Active Directory and login using your MS Office credentials

**Azure Active Directory** Link - <https://aad.portal.azure.com/>

#### 2. Create an Azure AD Application in your tenant

In the left side pane click the label **Azure Active Directory**. This will open up the blade for Azure Active Directory. In that screen you should see a label **App registrations**. This is the starting point of a registering an Azure AD Application. This blade will allow you to create a new application for Azure AD.

Click on the button **New registration** to create a new application.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Now you will see the new application registration blade

- **Name** This will be the name of your application.
- **Supported account types** This section will restrict the access.

Click **Register** button.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. You should see the newly registered applications blade

- **Application (client) ID** The id of your application.
- **Directory (tenant) ID** The Azure AD tenant id.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Allowing permissions for Microsoft Graph API

Click on the **API permissions** label.

Azure has already given you **User.Read** delegated permissions for your application. This permission will allow us to read user information for a logged in user. These are Microsoft Graph API permissions, we can also call them **Scopes**.

The full list of scopes for Microsoft Graph API - <https://learn.microsoft.com/en-us/graph/permissions-reference>.

Click on **+ Add a permission** button and select **Microsoft Graph**.

Click on **Delegated permissions**. Now you see a list of permissions available for Microsoft Graph API.

Select required permissions, click **Add permissions** button.

Click **Grant admin consent** button.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Allow public client flows

Specifies whether the application is a public client. Appropriate for apps using token grant flows that don't use a redirect URI.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Create a key for the application

![todo:image_alt_text](microsoft-graph-utility-features_5.png)
