# Endpoint "/status", ISO, Database, Connections e SQL Injections (Dia 20)
No [dia 16](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia16.md#endpoint) falamos sobre o que era Endpoint, dentre outras coisas que com certeza são úteis para esse dia 20. Aqui, vamos de fato implementar as coisas que queremos retornar quando acessamos o Endpoint `/status`.

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
