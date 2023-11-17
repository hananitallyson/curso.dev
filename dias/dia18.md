# Node-Postgres e Variáveis de Ambiente (Dia 18)
O dia 18 tem como foco a conclusão da tarefa `Criar módulo "database.js"`, e no caminho disso, vamos aprender sobre **Variáveis de Ambiente**, cujo o termo em inglês é **Environment Variable**.

No [dia anterior](/dias/dia17.md), decidimos utilizar o serviço PostgreSQL como nosso banco de dados. E para se comunicar com ele, instalamos o módulo [pg](https://www.npmjs.com/package/pg?activeTab=readme) no nosso projeto, pois ele sabe se comunicar no mesmo protocolo que o banco. Então nós utilizamos o **pg** para abrir uma conexão ao banco de dados e enviar uma query contra ele. E para retirar a necessidade de abrir uma conexão e fechar a mesma sempre que for enviar uma query, criamos a abstração `database.js`, onde basta executar o método `database.query()` definido nesse objeto para executar a consulta.

O [Node-postgres](https://node-postgres.com/) é uma coleção de módulos node.js para servir como interface para o banco de dados PostgreSQL, e vamos nos utilizar dessa abstração para realizar a conexão dentro da nossa própria abstração `database.js`.

```js
// database.js

import { Client } from "pg";

async function query(queryObject) {
  const client = new Client({
    host: process.env.POSTGRES_HOST,
    port: process.env.POSTGRES_PORT,
    user: process.env.POSTGRES_USER,
    database: process.env.POSTGRES_DB,
    password: process.env.POSTGRES_PASSWORD,
  });
  await client.connect();
  const result = await client.query(queryObject);
  await client.end();
  return result;
}

export default {
  query: query,
};
```

Primeiramente, vamos observar que é importamos a classe **Client** do módulo **pg** para depois instanciá-la como a constante `client`. Fazemos isso dentro da função assincrona `query()`, que recebe como parâmetro o valor `queryObject`. Essa função é assincrona devido o uso do operador **await** que espera pela **promise** para obter seu valor, e nesse caso esperamos pela conexão do cliente e pela finalização da conexão.

Dentro da instância de `client`, definimos os valores do banco de dados através das **variáveis de ambiente**: `host`, `port`, `user`, `database` e `password`.

# Variáveis de Ambiente
As **Environment Variables** ou **Variáveis de Ambiente**, são valores definidos pelo usuário do serviço que podem afetar a maneira como um processo em execução irá se comportar. Cada processo pode ler e escrever variáveis de ambiente. As variáveis podem ser usadas tanto por scripts quanto pela linha de comando.

Tais variáveis são parte do ambiente no qual um processo executa. Por exemplo, um processo do serviço de banco de dados PostgreSQL em execução pode consultar o valor da variável `POSTGRES_USER` para definir o nome do usuário do banco de dados que está sendo executado. Por convenção, as **variáveis de ambiente** são definidas por letras maiúsculas e são separadas por underlines ao invés de espaços em branco.

No caso da imagem docker do serviço do PostgreSQL, a única variável obrigatória, ou seja, que precisa ser definida pelo usuário de fato, é a `POSTGRES_PASSWORD`, usada para definir a senha do usuário que acessará o serviço. A `POSTGRES_USER` caso não seja especificada, define por padrão o valor como `postgres` para o nome do usuário. A variável `POSTGRES_DB` usada para definir o nome do banco de dados, se não definida, terá como valor o que estiver definido em `POSTGRES_USER`.

Em Unix, existe algumas variáveis em comum, algumas delas são:
- $PATH - lista de diretórios que são acessados durante uma busca do shell, por exemplo, para comandos globais do sistema (executáveis fora da pasta corrente).
- $HOME - diretório raiz do usuário atual.
- $LANG - locale padrão.

No terminal, é possível ler o valor armazenado em uma variável através do comando `echo`, por exemplo:
```sh
echo $LANG
# en_US.UTF-8
```
