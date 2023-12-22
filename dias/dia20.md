# Endpoint "/status", ISO, Database, MVC, Connections e SQL Injections (Dia 20)
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

## Arquitetura MVC
No [dia 14](https://github.com/hananitallyson/curso.dev/blob/main/dias/dia14.md) foi mencionado a arquitetura de software **MVC**, que significa **Model**, **Views** e **Controller**. Essa foi a arquitetura escolhida para nosso projeto, e nesse caso, o fluxo funciona da seguinte maneira.

Na visão do backend, o fluxo começa do **controller**, local onde entra a requisição do usuário, que nesse caso é um usuário pedindo as informações do endpoint `/status`. O **controller** se utiliza das ferramentas disponíveis no **model**. Sendo assim, o **controller** pede uma informação para o **model**, que por sua vez computa a informação ou executa alguma regra de negócio, e depois disso retorna a informação para o **controller**.

Por fim, o **controller**, após receber a informação do **model**, retorna essa informação para a **view**, para que ela possa apresentar isso ao usuário interessado, que nesse caso seria retornar as informações em formato JSON no `/status`.

### MVC sem Models
Uma das perguntas mais frequentes em relação ao MVC, é sobre a necessidade de criar a abstração de models. Muitos pensam que vale mais a pena desenvolver tudo no controller.

Bem, apesar de ainda ser funcional, isso não é a melhor abordagem. Sem os **models**, perdemos o que chamamos de **Reusability**, ou em português "Reutilizabilidade", que consiste na qualidade de reaproveitamento do nosso código. Sendo possível reutilizar uma mesma parte de código em locais distintos.

## SQL Injections
