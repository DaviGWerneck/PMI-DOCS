
Entendi! Pelo que você descreveu, você tem uma tabela chamada `conexao` no banco de dados `Guardian`, onde as informações de conexão para várias unidades são armazenadas. Esses dados podem ser utilizados para dinamicamente configurar a `ConnectionString` com base na unidade selecionada pelo usuário.

Para isso, o fluxo seria o seguinte:

1. **Consulta ao banco de dados `Guardian`** para buscar os dados de conexão da unidade selecionada.
    
2. **Montagem da `ConnectionString`** com os dados recebidos da tabela `conexao`.
    
3. **Uso da `ConnectionString`** para realizar a conexão com o banco correspondente à unidade selecionada.



### Passos para implementar isso:

#### 1. Modificar o Serviço para Buscar a Conexão no Banco

Você pode criar um serviço para buscar as informações da tabela `conexao` de acordo com a unidade e montar a `ConnectionString`. O serviço pode ser algo como:

```
public interface IConnectionStringProvider
{
    Task<string> GetConnectionStringAsync(int unidadeId);
}

public class ConnectionStringProvider : IConnectionStringProvider
{
    private readonly string _guardianConnectionString;
    private readonly IConfiguration _configuration;

    public ConnectionStringProvider(IConfiguration configuration)
    {
        _configuration = configuration;
        _guardianConnectionString = _configuration.GetConnectionString("Guardian"); // Conexão com o banco Guardian
    }

    public async Task<string> GetConnectionStringAsync(int unidadeId)
    {
        // Aqui você vai consultar o banco "Guardian" e pegar a configuração da unidade
        using (var connection = new SqlConnection(_guardianConnectionString))
        {
            await connection.OpenAsync();

            var query = @"
                SELECT CONSERVER, CONDBMS, CONDBMS, CONUSERNAME, CONPASSWORD
                FROM conexao
                WHERE CONCOD = @UnidadeId";
            
            var command = new SqlCommand(query, connection);
            command.Parameters.AddWithValue("@UnidadeId", unidadeId);

            using (var reader = await command.ExecuteReaderAsync())
            {
                if (await reader.ReadAsync())
                {
                    var server = reader["CONSERVER"].ToString();
                    var dbms = reader["CONDBMS"].ToString();
                    var dbName = reader["CONDBMS"].ToString(); // Isso seria o nome do banco de dados
                    var username = reader["CONUSERNAME"].ToString();
                    var password = reader["CONPASSWORD"].ToString();

                    // Agora você pode montar a ConnectionString
                    var connectionString = $"Data Source={server};Initial Catalog={dbName};User ID={username};Password={password};";
                    return connectionString;
                }

                throw new Exception("Unidade não encontrada");
            }
        }
    }

}

```


#### 2. Usando o Serviço no Controller

No controlador, você pode chamar o serviço para obter a `ConnectionString` com base no `unidadeId` (ou outro identificador que você usar para passar a unidade). Aqui está um exemplo de como usar esse serviço:
```

[ApiController]
[Route("api/[controller]")]
public class MeuController : ControllerBase
{
    private readonly IConnectionStringProvider _connectionStringProvider;

    public MeuController(IConnectionStringProvider connectionStringProvider)
    {
        _connectionStringProvider = connectionStringProvider;
    }

    [HttpGet("dados")]
    public async Task<IActionResult> GetDados(int unidadeId)
    {
        try
        {
            var connectionString = await _connectionStringProvider.GetConnectionStringAsync(unidadeId);

            // Agora você tem a connectionString da unidade e pode usar para conectar ao banco

            return Ok($"Conexão com a unidade {unidadeId} estabelecida.");
        }
        catch (Exception ex)
        {
            return BadRequest(ex.Message);
        }
    }
}



```


#### 3. Configuração do Banco e da Conexão

No código acima, estou fazendo uma consulta à tabela `conexao` no banco `Guardian` para obter a conexão da unidade selecionada. A partir dos dados de conexão que você tem na tabela, montamos a `ConnectionString` no formato adequado para o SQL Server.

### Exemplo de Retorno da Tabela `conexao`:

Considerando a tabela `conexao` que você forneceu, se o usuário solicitar, por exemplo, a unidade `UBS Esperança I - Produção` (código 16), o sistema vai consultar a tabela e montar a `ConnectionString` correspondente. O retorno pode ser algo como:

- **Servidor**: `SRV000088`
    
- **Banco de Dados**: `Sanitas_Producao`
    
- **Usuário**: Não fornecido (caso não seja uma conexão com autenticação do SQL)
    
- **Senha**: Não fornecida (novamente, se for autenticação integrada, por exemplo)
    

A `ConnectionString` gerada seria algo como:

`Data Source=SRV000088;Initial Catalog=Sanitas_Producao;Integrated Security=True;`

Se fosse uma conexão com usuário e senha:

`Data Source=SRV000088;Initial Catalog=Sanitas_Producao;User ID=usuario;Password=senha;`

### 4. Usando a `ConnectionString` para Consultar o Banco de Dados

Depois que você tiver a `ConnectionString`, você pode usá-la para se conectar ao banco de dados e fazer consultas ou manipulações conforme necessário.

Por exemplo, usando **Entity Framework Core**:

```
public async Task<IActionResult> GetDados(int unidadeId)
{
    var connectionString = await _connectionStringProvider.GetConnectionStringAsync(unidadeId);
    
    using (var context = new MeuDbContext(connectionString))
    {
        var dados = await context.MinhasTabelas.ToListAsync();
        return Ok(dados);
    }
}

```

