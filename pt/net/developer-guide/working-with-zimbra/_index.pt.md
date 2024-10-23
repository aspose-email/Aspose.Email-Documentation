---
title: "Trabalhando com Zimbra"
url: /pt/net/trabalhando-com-zimbra/
weight: 120
type: docs
---

## **Sobre o Zimbra**  

O Zimbra é uma suíte de email, calendário e colaboração construída para a nuvem. O Zimbra inclui email completo, contatos, calendário, compartilhamento de arquivos, tarefas e mensagens/videoconferência, tudo acessado a partir do Cliente Web Zimbra de qualquer dispositivo.  

## **Ler todas as mensagens do armazenamento TGZ do Zimbra**  

Aspose.Email fornece a classe TgzReader para ler arquivos de armazenamento TGZ do Zimbra. O seguinte código de exemplo demonstra o uso da classe TgzReader para ler todas as mensagens do arquivo.  

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}  

## **Obter contagem total de itens de um arquivo Tgz**  

O método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) da classe [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) retornará o número total de itens de mensagem contidos no armazenamento.  

O seguinte código de exemplo mostrará como implementar este método em seu projeto:  

```cs  
using (TgzReader reader = new TgzReader(fileName))  
{  
    int count = reader.GetTotalItemsCount();  
}  
```  

## **Salvar Mensagens e Estrutura de Diretórios**  

Você também pode salvar todas as mensagens com a estrutura de diretórios do arquivo de armazenamento TGZ do Zimbra. Para isso, a classe TgzReader fornece um método ExportTo que recebe o caminho de saída como parâmetro.  

O seguinte trecho de código demonstra o uso do método TgzReader.ExportTo para salvar todas as mensagens do arquivo de armazenamento TGZ do Zimbra.  

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}  

## **Exportar Itens de Calendário e Contato de Arquivos de Backup do Zimbra**  

Para exportar o calendário e contatos do Zimbra e salvá-los nos formatos iCalendar e VCard, você pode usar o seguinte trecho de código:  

```cs  
using (var reader = new TgzReader(@"test2.tgz"))  
{  
    //os arquivos de contatos podem ser encontrados nas subpastas Contatos e Contatos Enviados  
    //os arquivos de calendário podem ser encontrados na subpasta Calendário  
    reader.ExportTo(@"out");  
}  
```