---
title: "Por que não Automação"
url: /pt/net/why-not-automation/
weight: 40
type: docs
---

Por que os componentes Aspose são uma opção muito melhor do que a Automação do Microsoft Office. Existem duas perguntas que ouvimos com mais frequência aqui na Aspose:

1. **Seus produtos requerem que o Microsoft Office esteja instalado para que possam ser executados?**  
   A resposta simples é não. Os componentes Aspose são totalmente independentes e não estão afiliados, nem autorizados, patrocinados ou de alguma forma aprovados pela Microsoft Corporation.
2. **Por que devemos usar produtos Aspose em vez de utilizar a automação do Microsoft Office?**  
   A resposta mais curta que podemos dar é que existem muitas razões, sendo a principal que a própria Microsoft recomenda fortemente contra a automação do Office a partir de soluções de software: [Considerações para automação do Office no lado do servidor](https://support.microsoft.com/?scid=kb;EN-US;q257757). Existem várias razões pelas quais os componentes Aspose são uma alternativa melhor à automação. Alguns dos pontos-chave estão descritos abaixo. Além disso, não se esqueça de visitar os links no final desta seção.

## **Segurança**
A seguir está uma citação direta do artigo da Microsoft mencionado acima:

*"Aplicativos do Office nunca foram destinados para uso no lado do servidor, e, portanto, não levam em consideração os problemas de segurança enfrentados por componentes distribuídos. O Office não autentica solicitações recebidas, e não protege você de executar macros inadvertidamente ou iniciar outro servidor que possa executar macros, a partir do seu código do lado do servidor. Não abra arquivos que são enviados para o servidor de um Web anônimo! Com base nas configurações de segurança que foram definidas por último, o servidor pode executar macros sob um contexto de Administrador ou Sistema com plenos privilégios e comprometer sua rede! Além disso, o Office usa muitos componentes do lado do cliente (como Simple MAPI, WinInet e MSDAIPP) que podem armazenar informações de autenticação do cliente para acelerar o processamento. Se o Office estiver sendo automatizado no lado do servidor, uma instância pode atender mais de um cliente, e como as informações de autenticação foram armazenadas em cache para essa sessão, é possível que um cliente possa usar as credenciais em cache de outro cliente, obtendo assim permissões de acesso não concedidas ao se passar por outros usuários."*

Os produtos Aspose são muito seguros. Os componentes Aspose executam no mesmo contexto de usuário que todas as aplicações ASP.NET, sob o usuário ASPNET. Portanto, os componentes Aspose não representam um risco potencial para recursos vitais do sistema. Além disso, quando um documento é aberto por um componente Aspose, as macros não são executadas automaticamente. Os componentes Aspose foram projetados com o objetivo de permitir que os desenvolvedores criem, manipulem e salvem arquivos do Office. Nenhum dos riscos associados ao pacote do Microsoft Office é inerente aos componentes Aspose.

## **Estabilidade**
A seguir está uma citação direta do artigo da Microsoft mencionado acima:

*"Office 2000, Office XP e Office 2003 usam a tecnologia Microsoft Windows Installer (MSI) para facilitar a instalação e a autoconfiguração para um usuário final. O MSI introduz o conceito de "instalar no primeiro uso", que permite que recursos sejam instalados ou configurados dinamicamente em tempo de execução (para o sistema ou, mais frequentemente, para um usuário específico). Em um ambiente do lado do servidor, isso tanto desacelera o desempenho quanto aumenta a probabilidade de que uma caixa de diálogo apareça solicitando que o usuário aprove a instalação ou forneça um disco de instalação apropriado. Embora tenha sido projetado para aumentar a resiliência do Office como um produto para o usuário final, a implementação do Office das capacidades do MSI é contraproducente em um ambiente do lado do servidor. Além disso, a estabilidade do Office em geral não pode ser garantida quando executada no lado do servidor porque não foi projetada ou testada para esse tipo de uso. Usar o Office como um componente de serviço em um servidor de rede pode reduzir a estabilidade daquela máquina e, como consequência, a sua rede como um todo. Se você planeja automatizar o Office no lado do servidor, tente isolar o programa em um computador dedicado que não possa afetar funções críticas e que possa ser reiniciado conforme necessário."*

Como os componentes Aspose estão empacotados em uma única DLL, nunca haverá necessidade de instalar partes ou componentes adicionais para que funcionem. Os componentes Aspose são utilizados apenas por aplicações .NET e não há parte do código do componente projetado para aguardar uma resposta humana. Os componentes Aspose foram rigorosamente testados. Os componentes Aspose são utilizados por empresas como IBM, Hilton, Reader's Digest, Bank of America e muitas outras.

## **Escalabilidade/Veloz**
A seguir está uma citação direta do artigo da Microsoft mencionado acima:

*"Componentes do lado do servidor precisam ser componentes COM altamente reentrantes, multithreaded, com mínimo overhead e alta taxa de transferência para múltiplos clientes. Aplicativos do Office são, em quase todos os aspectos, exatamente o oposto. Eles são servidores de automação baseados em STA não reentrantes que são projetados para fornecer funcionalidades diversas, mas intensivas em recursos, para um único cliente. Eles oferecem pouca escalabilidade como solução do lado do servidor e têm limites fixos para elementos importantes, como memória, que não podem ser alterados por meio de configuração. Mais importante, eles usam recursos globais (como arquivos mapeados em memória, complementos ou templates globais e servidores de automação compartilhados), que podem limitar o número de instâncias que podem ser executadas simultaneamente e levar a condições de corrida se estiverem configurados em um ambiente de múltiplos clientes. Desenvolvedores que planejam executar mais de uma instância de qualquer Aplicativo do Office ao mesmo tempo precisam considerar "pooling" ou serializar o acesso ao Aplicativo do Office para evitar possíveis deadlocks ou corrupção de dados."*

Os componentes Aspose são altamente escaláveis e extremamente rápidos. Aplicativos do Office não foram projetados para serem usados simultaneamente por centenas e milhares de usuários; no entanto, os componentes Aspose foram projetados exatamente para isso. Nossos componentes são uma verdadeira solução .NET e funcionam perfeitamente, seja em um único servidor alimentando uma única aplicação ou em uma fazenda de web balanceada alimentando uma aplicação de uso em toda a empresa.

## **Preço**
Quando uma aplicação utiliza a automação do Microsoft Office, uma cópia do Microsoft Office deve ser comprada para cada máquina que executa a aplicação. Muitas vezes, uma aplicação pode precisar criar ou manipular um arquivo do Office, mas não requer que o usuário tenha o Office. A Aspose oferece uma licença de redistribuição muito econômica e livre de royalties que permitirá a implantação para um número ilimitado de usuários, sem preocupações de licenciamento.

Ao criar aplicativos baseados na web, é importante saber que os componentes de automação do Microsoft Office não são precificados nem licenciados para soluções do lado do servidor ([Licenciamento dos Componentes Web do Office 2000 e Extensões do Servidor Office](https://support.microsoft.com/?scid=kb;EN-US;q243006)); portanto, não existe uma boa solução de licenciamento para implantar aplicativos web que utilizam os componentes do Microsoft Office. A Aspose oferece uma solução muito econômica para aplicações baseadas em servidor também.

## **Recursos**
Os componentes Aspose fornecem tudo o que é necessário para gerenciar arquivos do Office, além de muito, muito mais. Eles são projetados com a filosofia de permitir que desenvolvedores alcancem os maiores resultados com o menor esforço. Ao contrário da automação do Office, os componentes Aspose oferecem muitas funções poderosas que economizam tempo. Por exemplo, Aspose.Cells oferece aos desenvolvedores a possibilidade de exportar de um **DataTable** ou **DataView** diretamente para um arquivo Excel. Aspose.Words oferece um recurso semelhante que permite aos desenvolvedores preencher um documento de mala direta do Word diretamente de qualquer objeto de dados .NET. Cada componente na família Aspose oferece seu próprio conjunto de recursos únicos e poderosos.

A melhor parte de comprar um componente Aspose ou um conjunto de componentes é ter acesso às nossas equipes de desenvolvimento. Nossas equipes de desenvolvimento reconhecem que se há um recurso que sua empresa precisa, é muito provável que outras empresas precisem dele também. Embora nem todos os pedidos de recursos possam ser adicionados, nossas equipes tentam ser muito abertas e flexíveis ao fornecer assistência. Essa mentalidade é o que ajudou os componentes Aspose a se tornarem tão poderosos quanto são. Se houver recursos adicionais que você precisa de objetos de automação do Office, suas chances de tê-los adicionados são muito, muito baixas.

## **Conclusão**
Este artigo abordou os pontos-chave sobre por que os componentes Aspose são uma escolha melhor do que a automação do Office. Todos os diferentes componentes Aspose oferecem uma versão de avaliação sem riscos e sem obrigações. Incentivamos você a aproveitar essa avaliação para ver o que a Aspose pode fazer por suas aplicações.

Para mais informações, consulte os seguintes artigos na Internet:

- [Top 10 Razões para Desenvolvedores Usarem o .NET Framework 1.1](http://msdn2.microsoft.com/en-us/netframework/aa497339.aspx)
- [Considerações para Automação do Office no Lado do Servidor](https://support.microsoft.com/?scid=kb;EN-US;q257757)[Licenciamento dos Componentes Web do Office 2000 e Extensões do Servidor Office](https://support.microsoft.com/?scid=kb;EN-US;q243006)