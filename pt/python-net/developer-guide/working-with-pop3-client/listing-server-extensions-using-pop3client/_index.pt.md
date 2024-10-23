---
title: "Listando Extensões de Servidor usando Pop3Client"
url: /pt/python-net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---
  
## **Listando Extensões de Servidor usando Pop3Client**  
O Pop3Client da Aspose.Email permite que você recupere as extensões de servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método GetCapabilities() retorna os tipos de extensão suportados na forma de um array de strings.  
### **Recuperando Extensões de Servidor**  
O seguinte exemplo de código demonstra a recuperação de extensões de servidor usando ImapClient para o servidor Gmail.  

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}  