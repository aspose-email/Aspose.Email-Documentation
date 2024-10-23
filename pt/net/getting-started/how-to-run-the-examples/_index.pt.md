---
title: "Como Executar os Exemplos"
url: /pt/net/how-to-run-the-examples/
weight: 90
type: docs
---


## **Requisitos de Software**
Por favor, assegure-se de que atende aos seguintes requisitos antes de baixar e executar os exemplos.

1. Visual Studio 2010 ou superior
1. Gerenciador de Pacotes NuGet instalado no Visual Studio. Certifique-se de que a versão mais recente da API NuGet está instalada no Visual Studio. Para detalhes sobre como instalar o gerenciador de pacotes NuGet, consulte <https://docs.microsoft.com/en-us/nuget/install-nuget-client-tools>
1. Vá para Ferramentas->Opções->Gerenciador de Pacotes NuGet->Fontes de Pacotes e certifique-se de que a opção **nuget.org** está marcada
1. O projeto de exemplo utiliza o recurso de Restauração Automática de Pacotes NuGet, portanto, você deve ter uma conexão de internet ativa.
## **Baixar do GitHub**
Todos os exemplos do Aspose.Font para .NET estão hospedados no [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET).

- Você pode clonar o repositório usando seu cliente GitHub favorito ou baixar o arquivo ZIP [aqui](https://docs.microsoft.com/en-us/nuget/install-nuget-client-tools).
- Extraia o conteúdo do arquivo ZIP para qualquer pasta em seu computador. Todos os exemplos estão localizados na pasta **Examples**.
- Os projetos são criados no Visual Studio 2013, mas os arquivos de solução são compatíveis com Visual Studio 2010 SP1 e superior.
- Abra o arquivo de solução no Visual Studio e compile o projeto.
- Na primeira execução, as dependências serão baixadas automaticamente via NuGet.
- A pasta **Data** na pasta raiz de **Examples** contém arquivos de entrada. É obrigatório que você baixe a pasta **Data** junto com o projeto de exemplos.
- Abra RunExamples.cs, todos os exemplos são chamados a partir daqui.
- Descomente os exemplos que você deseja executar dentro do projeto.

Sinta-se à vontade para nos contatar através de nossos fóruns se você tiver algum problema ao configurar ou executar os exemplos.
## **Contribuir**
Se você deseja adicionar ou melhorar um exemplo, incentivamos você a contribuir para o projeto. Todos os exemplos e projetos de demonstração neste repositório são de código aberto e podem ser usados livremente em suas próprias aplicações.

Para contribuir, você pode bifurcar o repositório, editar o código-fonte e criar um pull request. Revisaremos as alterações e as incluiremos no repositório, se consideradas úteis.