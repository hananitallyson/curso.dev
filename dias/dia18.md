# Node-Postgres e Variáveis de Ambiente (Dia 18)
O dia 18 tem como foco a conclusão da tarefa `Criar módulo "database.js"`, e no caminho disso, vamos aprender sobre **Variáveis de Ambiente**, cujo o termo em inglês é **Environment Variable**.

# Variáveis de Ambiente
As **Environment Variables** ou **Variáveis de Ambiente**, são valores definidos pelo usuário do serviço que podem afetar a maneira como um processo em execução irá se comportar. Cada processo pode ler e escrever variáveis de ambiente.

Tais variáveis são parte do ambiente no qual um processo executa. Por exemplo, um processo do serviço de banco de dados PostgreSQL em execução pode consultar o valor da variável `POSTGRES_USER` para definir o nome do usuário do banco de dados que está sendo executado. Por convenção, as **variáveis de ambiente** são definidas por letras maiúsculas e são separadas por underlines ao invés de espaços em branco.

No caso da imagem docker do serviço do PostgreSQL, a única variável obrigatória, ou seja, que precisa ser definida pelo usuário de fato, é a `POSTGRES_PASSWORD`, usada para definir a senha do usuário que acessará o serviço. A `POSTGRES_USER` caso não seja especificada, define por padrão o valor como `postgres` para o nome do usuário. A variável `POSTGRES_DB` usada para definir o nome do banco de dados, se não definida, terá como valor o que estiver definido em `POSTGRES_USER`.
