# api-restful-kcms

Olá, com base no desafio solicitado pela KCMS, consegui desenvolver uma API de Gerenciamento de Produtos conforme as diretrizes: https://github.com/kcmsbrasil/challenge-dev-backend, para atender uma grande varejista. Visto isso, os principais recursos utilizados para a criação dessa API foram:

     1. Criar novas categorias, listar as que já estão disponiveis, atualizar as informações de uma categoria existente e exclusão de categorias que não são mais necessárias, onde temos um controle melhor sobre a organização dos produtos.
     2. Com a API, é possivel criar novos produtos associados a categorias especificas, onde podemos listar os produtos ou até mesmo atualizar as informações já existentes em um produto ou remover-los. 
     3. Sugestão do uso NoSQL para facilitar e otimizar a pesquisa, consolidação e analise das informações, garantindo um armazenamento eficiente e escalável dos dados, podendo lidar de forma rápida e eficiente. 
     4. No código abaixo, é possivel visualizar uma arquitetura modular, separando e organizando as camadas de forma clara, objetiva e a responsabilidade entre as camadas da aplicação, tornando o código de fácil entendimento.
     5. Vale lembrar que não temos um ambiente de testes para integração desta API com o sistema real no momento, a estrutura do código pode permitir facilmente a adição e uma execução posterior de testes para garantir a qualidade e confiabilidade do código. 

    ProductManagementAPI
    ├── Controllers
    │   ├── CategoryController.cs
    │   └── ProductController.cs
    ├── Data
    │   ├── ICategoryRepository.cs
    │   ├── IProductRepository.cs
    │   ├── CategoryRepository.cs
    │   └── ProductRepository.cs
    ├── Models
    │   ├── Category.cs
    │   └── Product.cs
    ├── Services
    │   ├── ICategoryService.cs
    │   ├── IProductService.cs
    │   ├── CategoryService.cs
    │   └── ProductService.cs
    ├── Program.cs
    └── Startup.cs

____________________________________________________________________________________________________________________________

// Models
public class Category
{
    public string Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
}

public class Product
{
    public string Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string CategoryId { get; set; }
}

// Repositories
public interface ICategoryRepository
{
    Task<IEnumerable<Category>> GetCategoriesAsync();
    Task<Category> GetCategoryByIdAsync(string categoryId);
    Task CreateCategoryAsync(Category category);
    Task UpdateCategoryAsync(Category category);
    Task DeleteCategoryAsync(string categoryId);
}

public interface IProductRepository
{
    Task<IEnumerable<Product>> GetProductsByCategoryIdAsync(string categoryId);
    Task<Product> GetProductByIdAsync(string productId);
    Task CreateProductAsync(Product product);
    Task UpdateProductAsync(Product product);
    Task DeleteProductAsync(string productId);
}

public class CategoryRepository : ICategoryRepository
{
    // Implementação do repositório de categorias
}

public class ProductRepository : IProductRepository
{
    // Implementação do repositório de produtos
}

// Services
public interface ICategoryService
{
    Task<IEnumerable<Category>> GetCategoriesAsync();
    Task<Category> GetCategoryByIdAsync(string categoryId);
    Task CreateCategoryAsync(Category category);
    Task UpdateCategoryAsync(Category category);
    Task DeleteCategoryAsync(string categoryId);
}

public interface IProductService
{
    Task<IEnumerable<Product>> GetProductsByCategoryIdAsync(string categoryId);
    Task<Product> GetProductByIdAsync(string productId);
    Task CreateProductAsync(Product product);
    Task UpdateProductAsync(Product product);
    Task DeleteProductAsync(string productId);
}

public class CategoryService : ICategoryService
{
    private readonly ICategoryRepository _categoryRepository;

    public CategoryService(ICategoryRepository categoryRepository)
    {
        _categoryRepository = categoryRepository;
    }

    // Implementação dos métodos do serviço de categorias
}

public class ProductService : IProductService
{
    private readonly IProductRepository _productRepository;

    public ProductService(IProductRepository productRepository)
    {
        _productRepository = productRepository;
    }

    // Implementação dos métodos do serviço de produtos
}

// Controllers
[ApiController]
[Route("api/[controller]")]
public class CategoryController : ControllerBase
{
    private readonly ICategoryService _categoryService;

    public CategoryController(ICategoryService categoryService)
    {
        _categoryService = categoryService;
    }

    // Implementação dos métodos do controlador de categorias
}

[ApiController]
[Route("api/[controller]")]
public class ProductController : ControllerBase
{
    private readonly IProductService _productService;

    public ProductController(IProductService productService)
    {
        _productService = productService;
    }

    // Implementação dos métodos do controlador de produtos
}

// Program.cs e Startup.cs permanecem sem alterações

Para configurar o MongoDB, você pode utilizar o pacote NuGet MongoDB.Driver. E para a configuração do IoC Container, pode-se utilizar o padrão de injeção de dependência do ASP.NET Core.

Para rodar a aplicação, você pode seguir as instruções abaixo:

Clone o repositório.
Certifique-se de ter o .NET SDK instalado na sua máquina.
Configure o MongoDB localmente ou utilize um serviço de hospedagem.
Atualize as configurações de conexão com o banco de dados no arquivo appsettings.json.
Execute o comando dotnet run na pasta raiz do projeto.

Volto a reforçar o item 5 presente no inicio deste documento.

