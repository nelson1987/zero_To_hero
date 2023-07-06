# zero_To_hero
Repositorio sobre o curso Zero To Hero em NetCore

Ementa - Zero to Hero

Olá, eu somos: Nelson Neto, Alexandre Escossio e Yuri Dias, baseado em nossas experiências coorporativa, decidimos fazer essa trilha para que as pessoas que sentem interesse em trabalhar com estruturas corporativas programando em NetCore, possivelmente passará por alguns dos temas que abordaremos nessa ementa:

Padrões de Projeto
DDD/TDD/BDD
Clean Code
Clean Architecture
Nomenclatura
CQRS
Asíncrono
Performance
Remoção de valores nulos
versionamento
StatusCode
JWT
Swagger
Serilog
Rabbit
MassTransit
Fire-and-forget
Kafka
Kibana
ElasticSearch
MediatR
Observalidade
NewRelic
Escalabilidade
Automapper/Mapster
Ubuntu
Docker
.env - arquivo enviroment
.Yaml - arquivo Yaml
MiddleWareException
WSL
SQl/No-sql
Dapper
MongoDb
Oracle
SqlServer
Redis Cache
GZip e Brotli
HttpServerRequest
UnitTests
FunctionalTests
IntegrationTests
WebApi
...WebApp

1.Consulta de saldo da carteira
Os usuários podem usar a API para consultar o saldo atual de suas carteiras de investimentos.
Eles podem obter informações detalhadas sobre os ativos mantidos na carteira, incluindo o valor de mercado atual, a alocação de ativos e o desempenho geral da carteira.
[GET] /investments/{userLogin}
Response:
{
    "investments:[
        {
            "code": "PETR4",
            "value": 20.45,
            "amount":1
        },
        {
            "code": "CSEN4",
            "value": 10.96,
            "amount":2
        },
    ],
    "value": 32.37
}
 
2.Compra de ações
Os usuários podem usar a API para comprar ações de empresas listadas no mercado financeiro. Eles forneceriam os detalhes necessários, como o símbolo da ação e a quantidade desejada, e a API facilitaria a execução da transação.
[POST] /investments/buy
{
    "userLogin":"preston.tenent",
    "code": "PETR4",
    "value": 20.45,
   "amount": 1
}

3.Venda de ações
Os usuários podem vender as ações que possuem através da API. Eles forneceriam os detalhes da transação, como o símbolo da ação e a quantidade a ser vendida, e a API processaria a venda e atualizaria o saldo da carteira

[POST] /investments/sell
{
    "userLogin":"preston.tenent",
    "code": "PETR4",
    "value": 20.45,
    "amount": 1
}

public class Conta
{
    public string Login { get; set; }
    public decimal Valor { get; set; }
    public List<Investimento> Investimentos { get; set; }

    public void Comprar(Investimento investimento)
    {
        Investimentos.Add(investimento);
    }

    public void Vender()
    {
        Investimentos.Remove(investimento);
    }
}

public class Investimento
{
    public string Codigo { get; set; }
    public int Quantidade { get; set; }
    public decimal Valor { get; set; }
}
