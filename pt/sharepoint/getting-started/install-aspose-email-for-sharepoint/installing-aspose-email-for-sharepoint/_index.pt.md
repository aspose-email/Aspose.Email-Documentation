---
title: "Instalando Aspose.Email para SharePoint"
url: /pt/sharepoint/installing-aspose-email-for-sharepoint/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Aspose.Email para SharePoint pode ser baixado como o arquivo [Aspose.Email.SharePoint2010.zip](https://downloads.aspose.com/). 

{{% /alert %}} 
## **Instalação**
### **Conteúdo do Arquivo**
O arquivo Aspose.Email para SharePoint contém as pastas:

1. **Conversão de Email**: Converta formatos de arquivo de email e extraia anexos de arquivos EML e MSG em uma biblioteca de documentos.
1. **Sincronização de Email**: Sincronização de emails entre a lista personalizada de emails do SharePoint e o servidor de email.
1. **Sincronização da Biblioteca de Documentos**: Sincronização de arquivos entre a biblioteca de documentos e o servidor FTP.

Cada pasta contém o contrato de licença e os arquivos de instalação:

1. **arquivo wsp**: arquivo de solução do SharePoint. Aspose.Email para SharePoint é empacotado como uma solução do SharePoint para facilitar a implantação/retração em toda a fazenda de servidores.
1. **Aspose_LicenseAgreement.rtf**: contrato de licença do usuário final
1. **Setup.exe**: programa de instalação
1. **Setup.exe.config**: arquivo de configuração de instalação.

O programa de instalação verifica as seguintes condições antes de realizar a instalação:

1. SharePoint Foundation 2010 está instalado.
1. O usuário tem permissão para instalar soluções do SharePoint.
1. O serviço de Administração do SharePoint Foundation 2010 está iniciado.
1. O serviço Timer do SharePoint Foundation 2010 está iniciado.

{{% alert color="primary" %}} 

O serviço de Administração do WSS e o serviço Timer são necessários porque algumas ações de instalação dependem de um trabalho de temporizador para se propagar a todos os servidores na fazenda de servidores.

{{% /alert %}} 
### **Instalando Aspose.Email**
Para instalar Aspose.Email para SharePoint:

1. Descompacte o SIP do Aspose.Email para SharePoint na unidade local do servidor SharePoint 2010.
1. Execute o Setup.exe e siga as instruções na tela. O programa de instalação realiza as seguintes ações:
   1. Verifica os pré-requisitos de instalação. A instalação não continuará se qualquer verificação falhar. 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_1.png)




1. Exibe o contrato de licença do usuário final. O usuário deve aceitar o contrato para prosseguir 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_2.png)




1. Instala e implanta o recurso na fazenda de servidores 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_3.png)