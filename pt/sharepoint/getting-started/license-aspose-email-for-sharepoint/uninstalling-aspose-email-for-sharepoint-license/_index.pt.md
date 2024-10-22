---
title: "Desinstalando a Licença do Aspose.Email para SharePoint"
url: /pt/sharepoint/uninstalling-aspose-email-for-sharepoint-license/
weight: 30
type: docs
---

Para desinstalar a licença do Aspose.Email para SharePoint, use o console do servidor ou o SharePoint 2010 Management Shell:

1. Revogue a solução da licença da farm: 

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Execute tarefas administrativas para completar a revogação imediatamente: 

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Aguarde a conclusão da revogação. Use a Administração Central para verificar se a revogação foi concluída: 
   1. Em **Administração Central**, selecione **Operações** e depois **Gerenciamento de Soluções**.
1. Remova a solução do repositório de soluções do SharePoint: 

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```