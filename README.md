# api-restful-kcms

Olá, com base no desafio solicitado pela KCMS, consegui desenvolver uma API de Gerenciamento de Produtos conforme as diretrizes: https://github.com/kcmsbrasil/challenge-dev-backend, para atender uma grande varejista. Visto isso, os principais recursos utilizados para a criação dessa API foram:

Sobre o Projeto

Esta API oferece uma variedade de recursos para facilitar o gerenciamento de produtos:

Gestão de Categorias:
Permite criar novas categorias para organizar os produtos.
Lista as categorias existentes para fácil referência.
Possibilita atualizar ou remover categorias conforme necessário.

Gestão de Produtos:
Permite adicionar novos produtos associados a categorias específicas.
Oferece a capacidade de visualizar, atualizar e remover produtos do sistema.

Armazenamento NoSQL:
Optamos por utilizar um banco de dados NoSQL para garantir uma experiência de armazenamento eficiente e escalável.
Isso nos permite lidar facilmente com grandes volumes de dados e otimizar operações de pesquisa e análise.

Arquitetura Modular:
Implementamos uma arquitetura modular para garantir a organização e a clareza do código.
Cada camada da aplicação tem suas responsabilidades bem definidas, facilitando a manutenção e a evolução do sistema.

Testes e Qualidade do Código:
Embora ainda não tenhamos um ambiente de testes integrado, nossa estrutura de código está pronta para suportar testes unitários e de integração no futuro.
A qualidade e a confiabilidade do código são prioridades para nós, e estamos comprometidos em garantir que nossa API seja robusta e livre de erros.

____________________________________________________________________________________________________________________________

Modelos (Models):
Aqui definimos como serão estruturadas as informações das categorias e dos produtos. As categorias têm um ID, nome e descrição, enquanto os produtos têm um ID, nome, descrição, preço e o ID da categoria à qual pertencem.

Repositórios (Repositories):
Os repositórios são como "pontes" entre nosso código e o banco de dados. Eles nos permitem buscar, criar, atualizar e excluir informações do banco. Por exemplo, podemos usar o ICategoryRepository para encontrar categorias, adicionar novas ou deletar categorias existentes.

Serviços (Services):
Os serviços são onde fica a "inteligência" do nosso sistema. Eles contêm a lógica de negócios por trás das operações que realizamos com categorias e produtos. Por exemplo, o CategoryService tem métodos para encontrar, adicionar, atualizar e excluir categorias.

Controladores (Controllers):
Os controladores são a "porta de entrada" da nossa API. Eles recebem as requisições HTTP dos usuários e as direcionam para os serviços adequados. Por exemplo, o CategoryController lida com solicitações relacionadas a categorias, como buscar, adicionar, atualizar e excluir categorias.

Para configurar o MongoDB, você pode utilizar o pacote NuGet MongoDB.Driver. E para a configuração do IoC Container, pode-se utilizar o padrão de injeção de dependência do ASP.NET Core.

Para rodar a aplicação, você pode seguir as instruções abaixo:

Clonar o repositório do GitHub na sua máquina.
Certifique-se de ter o .NET SDK instalado na sua máquina.
Configure o MongoDB localmente ou utilize um serviço de hospedagem.
Atualize as configurações de conexão com o banco de dados no arquivo appsettings.json.
Execute o comando dotnet run na pasta raiz do projeto.

Volto a reforçar o item 5 presente no inicio deste documento.

