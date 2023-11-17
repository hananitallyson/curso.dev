# Fundamentos: Database, Docker e Containers (Dia 17)
Nesse dia 17, nós vamos falar sobre assuntos mais do que fundamentais, são assuntos primordiais! O Filipe traz nesse dia, os seguintes temas: Introdução a **Database**, **Docker** e como **Containers** funcionam. Vamos começar com o assunto principal: **Database** ou "Banco de Dados". 

## Database
Primeiramente, o que é uma **database** ou **banco de dados**? Em resumo, um **banco de dados** é uma coleção estruturada de dados, como por exemplo, um caderno com as informações dos clientes de uma loja. Nesse exemplo, os dados são armazenados em papéis e escritos por caneta ou lápis. Em nosso contexto de desenvolvimento, os dados são armazenados de forma eletrônica dentro de um computador, no entanto, a ideia continua a mesma do caderno: armazenar dados sobre coisas.

Mas o que são **dados**? Em resumo, dados são valores atribuídos a algo. Lembrando que tais valores não precisam ser necessariamente números, por exemplo, o nome e idade de um cliente. A idade é um valor númerico, mas o nome é uma informação textual.

Antes de criar um banco de dados, muitas organizações passam pela **Modelagem de Dados** que consiste na criação de um esquema visual do banco de dados, e tem como principais objetivos: evitar a redundância de dados, evitar inconsistência de dados e facilitar atualizações do banco. Para mais informações sobre modelagem, fica a recomendação do repositório do meu amigo e colega Charlon: [MySQL - Modelagem](https://github.com/charlon-156/MySQL/blob/main/Modelagem.md#modelagem-de-dados).

E para estudar ainda mais os conteúdos de database e modelagem, veja os links abaixo para acessar alguns artigos.
- [O que é um Banco de Dados? - Oracle](https://www.oracle.com/br/database/what-is-database/)
- [O que é modelagem de dados? - Amazon](https://aws.amazon.com/pt/what-is/data-modeling/)

### Data Base Management System (DBMS)
**Data Base Management System** ou "Sistema de Gerenciamento de Banco de Dados (SGBD)" é um sistema que será utilizado para gerenciar um ou mais bancos de dados e define como os dados serão armazenados. Existem diversos **SGBDs**, como:  Oracle, SQL Server, DB2, PostgreSQL, MySQL, e outros. No fim, o objetivo de todos é o mesmo: retirar da aplicação a responsabilidade de gerenciar e manipular o banco de dados. 

Muitas vezes dentro da nossa área quando falamos em banco de dados, queremos na realidade nos referir a um **SGBD**. Quando, por exemplo, falamos: "Vamos usar o PostgreSQL como nosso banco de dados". Estamos na realidade dizendo que vamos usar o gerenciador de banco de dados PostgreSQL.

Tais sistemas possuem também diferentes tipos e consequentemente diferentes objetivos, os dois principais são os **Relacionais** e os **Não Relacionais**, ou **SQL** e **NoSQL**.

**SQL** é um acrônimo para **Structured Query Language** ou "Linguagem de Consulta Estruturada". A linguagem declarativa **SQL** foi desenvolvida pela primeira vez na IBM nos anos 1970 e ainda é amplamente usada até hoje. Para saber mais sobre SGBDs e SQL, veja os links abaixo.

- [Sistema de gerenciamento de banco de dados - Wiki](https://pt.wikipedia.org/wiki/Sistema_de_gerenciamento_de_banco_de_dados)
- [Saiba tudo sobre SQL: A linguagem padrão para trabalhar com banco de dados relacionais! - Alura](https://www.alura.com.br/artigos/o-que-e-sql)

### Query e ORM
**Query** tem vários significados, como "Pergunta" e "Questão", mas no contexto de bancos de dados tem o significado de "Consulta". Uma **query** funciona como um componente que permite a inserção, atualização, seleção e exclução de dados dentro de um banco. Para criarmos uma **query** é preciso usar uma linguagem, e a mais conhecida das linguagens já foi mencionada anteriormente: a **Structured Query Language (SQL)**.

Uma **ORM**, acrônimo para **Object-Relational Mapping** ou "Mapeamento Objeto-Relacional", é uma abstração que serve para facilitar a relação entre o paradigma relacional dos bancos de dados e o desenvolvimento de uma aplicação. Então, ao invés de ser necessário escrever as **queries**, ou seja as **consultas** ao banco de dados, de forma manual como:
```sql
SELECT count(*) FROM users;
```
Podemos usar uma **ORM** e consultar o banco através de métodos e funções de uma linguagem de programação. Seguindo a lógica do último exemplo, em uma **ORM** a **query** poderia ser feita da seguinte maneira:
```js
User.count();
```
Isso então será transformado em uma **query** de verdade e será executada contra o banco de dados.

No geral, a **ORM** vem para facilitar o trabalho no desenvolvimento, no entanto, não é algo obrigatório e tem os seus prós e contras, como ser mais fácil de fazer implementações, mas quando queremos fazer uma consulta mais complexa pode ser mais dificil.

Dentro do curso.dev escolhemos não usar nenhuma ORM para realizar as **queries**, ao invés disso preferimos escrever as consultas na mão. Para realizar a conexão com o banco, usamo o módulo [pg](https://www.npmjs.com/package/pg?activeTab=readme) que é um cliente PostgreSQL sem bloqueio para Node.js.

### Migrations
De forma simplificada, uma **Migration** ou em português "Migração", é um arquivo que instrui e serve como forma de gerenciar as mudanças na estrutura do banco de dados de uma aplicação. Permitindo diversas alterações relacionadas as tabelas, índices e dentre outros elementos.

É com as **migrations** que se torna possível "versionar" o seu banco de dados, uma vez que esses arquivos podem ser enviados através de git para um repositório. Elas também servem para garantir que as mudanças da estrutura do banco dentro da **homologação** são as mesmas dentro da **produção**. Se você quer entender melhor sobre migrations, veja o link abaixo.

- [Migrations - Kenzie](https://kenzie.com.br/blog/migrations/)

## Docker e Containers
Agora, vamos falar um pouco sobre **infraestrutura**. Quando falamos sobre **infraestrutura**, estamos nos referindo aos componentes necessários para executar e gerenciar ambientes, que nesse caso, é um ambiente de desenvolvimento e produção de uma aplicação. Isso envolve sistema operacional, hardware, patches de seguranças, softwares, dentre outras coisas.

Antigamente, para gerenciar serviços da infraestrutura, como o próprio banco de dados, eram utilizados **Virtual Machines (VM)** (_Máquinas Virtuais_), pois dessa forma é possível "igualar" máquinas **hosts** que hospedavam o serviço. Uma vez que essas **VMs** permitiam que, mesmo sendo manualmente, a gente configurasse uma nova máquina dentro da nossa própria máquina, diminuindo a inconsistência da infraestrutura.

Mas só usar um virtualizador não era o suficiente, seja por causa da escala da equipe de desenvolvimento, ou pelo custo de memória e processamento que envolvia virtualizar um novo sistema completo dentro de outro sistema, que nesse caso é o da máquina em si. Além disso, era preciso ter uma nova máquina virtual para cada camada da aplicação, como um para o serviço de e-mail, um para o banco de dados, e outros. No entanto, em 2013, Solomon Hykes criou o **Docker** em cima dos recursos Linux: **PID Namespaces** e **cgroups**.

O **PID Namespaces** é um identificador usado pelo sistema para rastrear uma tarefa específica em um computador. Através disso, o **Docker** executa cópias idênticas de um software mesmo se tais softwares não foram escritos para ter mais de uma cópia aberta ao mesmo tempo, isolando o PID para que ele não fique ciente do que está acontecendo fora de seus próprios processos, como se houvesse uma membrana ao seu redor.

Enquanto o **Control Groups**, conhecido também só por **cgroups**, serve para o **Docker** limitar, contabilizar e isolar o uso de recursos de uma máquina para um grupo de processos.

E é assim que surge a ideia de **Container**, que nada mais é do que um ambiente **isolado**, disposto em um servidor. Então quando temos vários serviços, podemos sepoará-los em **containers**, e todos eles vão dividir uma única máquina host, economizando bastante o custo de memória e processamento.

### Usando Docker e Docker Compose
Para usar o **Docker** existe o comando de mesmo nome: `docker`. Através deste comando, podemos fazer tudo que é necessário para colocar um container para rodar. Com o subcomando `docker compose` é possível construir e gerenciar serviços em containers.

Primeiramente, dentro do nosso projeto é preciso ter um arquivo chamado `compose.yaml`, que é um arquivo de configuração resposável por listar os serviços e de onde está vindo a **docker image** desse serviço. Esse **docker image**, ou imagem docker é um binário resultante da compilação de um **dockerfile**, ou seja, um arquivo docker. E o container é uma imagem docker em funcionamento. É por causa disso, que podemos usar imagens prontas, ou seja, que foram já foram compiladas. Baixando essas imagens de repositórios como o [DockerHub](https://hub.docker.com/). Abaixo, um exemplo de `compose.yaml` usado para rodar um banco de dados PostgreSQL.

```yaml
# compose.yaml

services:
  database:
    image: "postgres:16.0-alpine3.18"
    environment:
      POSTGRES_PASSWORD: "local_password" # O valor da senha pode ser alterado
```

Como dito anteriormente, usando o `docker compose` podemos **levantar** (_Up_) o container com as informações descritas no `compose.yaml`.
```sh
docker compose up
```

Para **derrubar** (_Down_) o serviço, usando o comando abaixo:
```sh
docker compose down
```

---

- [Anterior](/dias/dia16.md) - [Próximo](/dias/dia18.md) - [Sumário](../README.md)
