# Endpoint "/status", Database, SQL Injections e mais (Dia 20)
No [dia 16](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia16.md#endpoint) falamos sobre o que era Endpoint, dentre outras coisas que com certeza são úteis para esse dia 20. Aqui, vamos de fato implementar o que queremos retornar quando acessamos o endpoint `/status`, além de passar vários outros conteúdos que serão de grande importância para o nosso desenvolvimento. Então, se preparem, pois esse dia tem de tudo para ser o mais longo dos dias até agora.

## Updated_at e ISO
A primeira propriedade do objeto JSON que queremos retornar é a `updated_at`, cuja sua função é retornar o momento exato na qual os dados do objeto foram gerados lá no backend.

```json
{
  "updated_at": "2023-12-21T16:14:07.403Z"
}
```

Esse dado está no formato conhecido como ISO 8601, um padrão muito comum formado por ano, mês, dia, seguido da hora, minuto e segundo. Além disso, é possível observar a letra `T` de "Time" que separa a data do horário, e por fim, a letra `Z` que indica a **time zone**, ou fuso horário. Essa letra faz referência ao sistema de [fuso horário militar](https://en.wikipedia.org/wiki/Military_time_zone), onde o `Z` é de "Zulu Time Zone" e que significa um desvio de UTC+00:00.

## Dependencies
A segunda propriedade do objeto JSON, é a `dependencies`, que por sua vez é um outro objeto que serve para mostrar as informações sobre as dependências usadas no nosso projeto. Nesse caso, vamos mostras as informações sobre os status do nosso banco de dados.

```json
{
  "updated_at": "2023-12-21T16:14:07.403Z",
  "dependencies": {
    "database": {
      "max_connections": 100,
      "opened_connections": 1,
      "version": "16.0"
    }
  }
}
```

Como é possível ver, as informações que vamos apresentar sobre nosso banco de dados são max_connections, opened_connections e version. Respectivamente, o máximo de conexões que a instância consegue suportar, o número de conexões abertas, e por fim, a versão do banco de dados.

### Database Version
Vamos começar pela versão do nosso banco de dados. Para fazer isso, precisamos acessar essa informação de alguma maneira. Como queremos algo relacionado ao banco de dados, podemos ter essa informação consultando o próprio banco de dados.

Bem, já sabemos que temos que realizar uma query, uma consulta, ao nosso banco de dados, mas qual dos tipo principais de consulta vamos utilizar: **SELECT**, **UPDATE**, **DELETE** ou **SHOW**?

**SELECT:** A query SELECT é usada para recuperar dados de uma ou mais tabelas em um banco de dados. Com ela, você pode especificar as colunas que deseja recuperar, condições para filtrar os resultados e até mesmo realizar operações em dados, como soma ou até mesmo contagem.
```sql
SELECT dado FROM tabela;
```

**UPDATE:** A query UPDATE é usada para modificar os dados existentes em uma tabela. Com ela, é possível atualizar os valores em uma ou mais colunas com base em condições especificadas.
```sql
UPDATE tabela SET dado = novo_dado WHERE dado = 'antigo_dado';
```

**DELETE:** A query DELETE é empregada para remover registros de uma tabela com base em determinadas condições. Tenha cuidado ao usá-la, pois ela exclui dados de forma permanente.
```sql
DELETE FROM tabela WHERE dado = 0;
```

**SHOW:** A query SHOW não é uma operação padrão de manipulação de dados. Em vez disso, ela é usada para exibir informações sobre o banco de dados, como tabelas, colunas, índices, entre outros.
```sql
SHOW TABLES;
```

Nesse caso, como queremos apenas exibir a informação da versão do nosso banco de dados, o mais indicado é o **SHOW**. E o código ficaria mais ou menos assim:
```javascript
const databaseVersion = (await database.query("SHOW server_version;")).rows[0].server_version;
```
Primeiro, executamos a query através da nossa abstração database e esperamos o resultado. Em seguida, acessamos o `rows[0]`, pois um banco de dados relacional sempre retorna uma lista mesmo se pedirmos uma única coisa, e de lá pegamos o `server_version` com a informação que queremos.

### Connections
Agora, precisamos exibir a quantidade máxima de conexões do nosso banco de dados, e como eu usei a palavra "exibir", já sabemos que vamos usar o `SHOW` para acessar essa informação na nossa consulta ao banco. 
```javascript
const databaseMaxConnections = (await database.query("SHOW max_connections;")).rows[0].max_connections;
```

Por fim, vamos exibir a quantidade de conexões abertas. Nesse caso, nós vamos precisar acessar e recuperar esse dado de uma tabela, para isso vamos usar o `SELECT`.
```javascript
const databaseOpenedConnections = (
  await database.query({
    text: "SELECT count(*)::int FROM pg_stat_activity WHERE datname = $1;",
    values: [databaseName],
  })
).rows[0].count;
```
Se você observar bem, esse código está bem diferente dos demais. Isso porque nosso código está protegido de **SQL Injections**, para saber mais sobre isso, veja em [SQL Injections](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia20.md#sql-injections).

Explicando um pouco mais essa consulta... Basicamente, nós acessamos a tabela `pg_stat_activity` do nosso banco de dados, e em seguida fizemos a contagem em números inteiros da quantidade de conexões abertas. A separação entre `text` e `value` é basicamente uma funcionalidade do **node-postgres** chamada de [Parameterized Query](https://node-postgres.com/features/queries#parameterized-query), ou em português, "Consultas Parametrizadas".

## Arquitetura MVC
No [dia 14](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia14.md) foi mencionado a arquitetura de software **MVC**, que significa **Model**, **Views** e **Controller**. Essa foi a arquitetura escolhida para nosso projeto, e nesse caso, o fluxo funciona da seguinte maneira.

Na visão do backend, o fluxo começa do **controller**, local onde entra a requisição do usuário, que nesse caso é um usuário pedindo as informações do endpoint `/status`. O **controller** se utiliza das ferramentas disponíveis no **model**. Sendo assim, o **controller** pede uma informação para o **model**, que por sua vez computa a informação ou executa alguma regra de negócio, e depois disso retorna a informação para o **controller**.

Por fim, o **controller**, após receber a informação do **model**, retorna essa informação para a **view**, para que ela possa apresentar isso ao usuário interessado, que nesse caso seria retornar as informações em formato JSON no `/status`.

### MVC sem Models
Uma das perguntas mais frequentes em relação ao MVC, é sobre a necessidade de criar a abstração de models. Muitos pensam que vale mais a pena desenvolver tudo no controller.

Bem, apesar de ainda ser funcional, isso não é a melhor abordagem. Sem os **models**, perdemos o que chamamos de **Reusability**, ou em português "Reutilizabilidade", que consiste na qualidade de reaproveitamento do nosso código. Sendo possível reutilizar uma mesma parte de código em locais distintos.

## Os 3 Estágios do TDD
No [dia 15](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia15.md), falamos sobre a técnica de desenvolvimento chamada de **TDD**. Hoje, vamos detalhar os seus 3 estágios: **Red**, **Green** e **Refactor**.

O primeiro estágio é o **Red**, que em inglês é a cor vermelha, e faz referência a cor que indica falha no teste. É nessa etapa que escrevemos um teste que espera algo que não é atendido. Naturalmente, o segundo estágio, **Green**, que em inglês é a cor verde, é quando fazemos a implementação concetra do nosso código que atende ao esperado pelo teste.

Por fim, o último estágio é o **Refactor** ou "Refatoração". Esse estágio consiste no processo de melhorar o código da nossa implementação sem alterar o resultado final. Basicamente, o processo de **refatoração** é quando alteramos nosso código tornando-o mais semântico sem mudar em nada o resultado daquela implementação.

## SQL Injections
