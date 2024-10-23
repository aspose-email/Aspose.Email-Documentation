---
title: "Instalando a Licença Aspose.Email para SharePoint"
url: /pt/sharepoint/installing-aspose-email-for-sharepoint-license/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Uma vez que você esteja satisfeito com sua avaliação, você pode [comprar uma licença](http://www.aspose.com/purchase/default.aspx). Antes de comprar, certifique-se de entender e concordar com os termos da licença.

A licença é enviada por e-mail após o pagamento do pedido. A licença é um arquivo ZIP que contém um pacote de solução regular do SharePoint.

O arquivo ZIP contém:

- **Aspose.Email.SharePoint.License.wsp**: arquivo do pacote de solução do SharePoint. A licença Aspose.Email para SharePoint é empacotada como uma solução do SharePoint para facilitar a implantação/retratação através da fazenda de servidores.
- **readme.txt**: instruções de instalação da licença. A licença é instalada a partir do console do servidor via o arquivo stsadm.exe. As etapas necessárias para instalar a licença estão detalhadas abaixo.

{{% /alert %}} 
## **Instalando a Licença a partir da solução WSP**
Nas instruções abaixo, os caminhos são omitidos para clareza. Você pode precisar adicionar o caminho real para o stsadm.exe e/ou arquivo da solução ao executá-los.

Para instalar a licença Aspose.Email:

1. Execute o SharePoint 2010 Management Shell.
1. Execute o stsadm para adicionar a solução à solução do SharePoint: 

```java

 stsadm.exe \-o addsolution \-filename Aspose.Email.SharePoint.License.wsp

```

1. Implante a solução em todos os servidores da fazenda: 

```java

  stsadm.exe \-o deploysolution \-name Aspose.Email.SharePoint.License.wsp \-immediate --force

```

1. Execute trabalhos temporizados administrativos para concluir a implantação imediatamente: 

```java

 stsadm.exe \-o execadmsvcjobs

```

Se o serviço de Administração do Windows SharePoint Services não tiver sido iniciado quando você implantou a licença, um erro será exibido. O Stsadm.exe depende desse serviço e do Serviço de Temporizador do Windows SharePoint para replicar dados da solução pela fazenda. Se esses serviços não estiverem em execução em sua fazenda de servidores, você pode precisar implantar a licença em cada servidor. 

![todo:image_alt_text](installing-aspose-email-for-sharepoint-license_1.png)
## **Instalando a Licença a partir do arquivo LIC**
Para instalar a licença a partir do arquivo Lic, você precisa colocar o arquivo de licença na pasta Aspose.Network.SharePoint.License da seguinte forma:

`InstalledDrive\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\Template\Features\Aspose.Network.SharePoint.License`

Os seguintes nomes de Licença são reconhecidos pela API Aspose.Email para SharePoint:

1. Aspose.Network Product Family.lic
1. Aspose.Email.SharePoint.lic
1. Aspose.Email Product Family.lic
1. Aspose.Total for SharePoint.lic
1. Aspose.Total Product Family.lic