---
title: "Solução de Problemas na Instalação"
url: /pt/sharepoint/troubleshooting-installation/
weight: 40
type: docs
---


## **Erro: Algumas ou todas as referências de identidade não puderam ser traduzidas**
Se você ver erros como “Algumas ou todas as referências de identidade não puderam ser traduzidas”, você pode executar o seguinte comando para resolvê-los.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMÍNIO\username> -password <senha>



```

{{% alert color="primary" %}} 

Se a mensagem de erro "Algumas ou todas as referências de identidade" aparecer, você também pode precisar reiniciar os serviços do IIS usando “iisreset” ou reiniciar o sistema operacional. 

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}