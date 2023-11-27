# Absolute Imports, Services Scripts, ENV e Credentials (Dia 19)
O dia 19 foi cheio de configuração, mexemos com `jsconfig.json` para nossas importações, `package.json` para nossos scripts, e `.env` para armazenar nossas variáveis de ambiente.

## Absolute Imports
Tanto o **Absolute Imports**, quanto o **Relative Imports** são maneiras de importar componentes dentro do nosso código em um projeto. No entanto, o **Relative Imports**, se utiliza do caminho **relativo** do componente em relação ao código em que ele é importado, e por muitas vezes gera um emaranhado de `../` na importação. Por exemplo:
```js
import database from "../../../../infra/database.js";
```
O **Absolute Imports** por outro lado, se utiliza do caminho **absoluto** do projeto, tornando o código muito mais limpo e organizado. Por exemplo:
```js
import database from "infra/database.js";
```
### BaseURL
Para configurarmos o **Absolute Imports** dentro do nosso projeto, vamos precisar criar um arquivo chamado `jsconfig.json` dentro do diretório raiz. A presença do arquivo de configuração `jsconfig.json` em um diretório indica que o mesmo é o diretório raiz do projeto JavaScript. Dentro desse arquivo, vamos definir a `baseUrl` do nosso projeto como `.`, indicando o caminho absoluto da raiz do projeto.
```json
{
  "compilerOptions": {
    "baseUrl": "."
  }
}
```

### O que acontece se deixarmos o `/` no inicio do import?
Nos comentários da aula sobre configuração do **baseUrl**, algumas pessoas apresentaram os comportamentos diferentes do seus códigos. A pessoa `marini` comentou:
>O meu já estava funcionando com import database from "/infra/database.js"; mesmo sem o arquivo jsconfig.json. Única diferença do meu caminho pro caminho do vídeo é que o meu caminho começava com uma /. Tinha feito essa alteração >numa aula que o Filipe tinha perguntado...
>Será que se remover esses "../../../" a aplicação vai quebrar?
>aí eu testei e não quebrou, por isso eu acabei deixando assim, mas pelo que eu entendi no vídeo, não era esse o comportamento esperado. Será que não precisa mais do arquivo de config do javascript json?

E o aluno `andrecruzmendes` respondeu trazendo as seguintes informações que irei parafrasear a seguir.

Quando `/` não está presente no início do **imports**, o caminho será interpretado como **relativo**, levando em consideração o diretório do arquivo atual como ponto de partida. Porém, se o **imports** começar com `/` indicamos que o caminho é **absoluto**.
```js
import database from "/infra/database.js";
```
Dessa forma, como o Node.js resolve caminhos absolutos a partir da raiz do sistema de arquivos do sistema operacional teriamos um erro, porém o Next.js, quando executado pelo comando `npm run dev`, considera o diretório de trabalho no terminal como sendo o ponto de partida, e geralmente esse diretório é a raiz do projeto.

Além disso, o Next.js assume a localização do arquivo `package.json` como sendo a raiz do projeto e utiliza esse caminho em absolute imports mesmo em ambiente de produção. Apesar de não haver documentação oficial sobre isso. Assim, o nosso código teoricamente funciona sem quebrar. 

Mas, para garantir segurança, o ideal é manter o arquivo `jsconfig.json` com o `baseUrl`.

## Scripts
Para acelerar a inicialização de serviços no nosso projeto, o Felipe nos ensinou a como criar scripts para isso. Abaixo estão os comandos relacionados aos nossos serviços, que por enquanto é somente o banco de dados.

Aqui subimos nosso serviço usando aquele comando do **docker compose**:
```sh
npm run services:up # docker compose -f infra/compose.yaml up -d
```

E aqui, paramos o nosso serviço, mas não derrubamos ele:
```sh
npm run services:stop # docker compose -f infra/compose.yaml stop
```

Aqui, no entanto, derrubamos o serviço:
```sh
npm run services:down # docker compose -f infra/compose.yaml down
```

Por último, para deixar ainda mais rápido a inicialização, unimos o comando do **next** mais o nosso **script** usando o operador **&&**, quando usamos isso, garantimos que o segundo comando será executado somente quando o primeiro já tiver sido executado com sucesso.
```sh
npm run dev # npm run services:up && next dev
```

## Fazer Commit do .env é correto?
De acordo com a documentação oficial do [DotENV](https://nextjs.org/docs/pages/building-your-application/configuring/environment-variables#default-environment-variables):
>**No. We strongly recommend against committing your .env file to version control.** It should only include environment-specific values such as database passwords or API keys. Your production database should have a different password than your development database.

Enquanto na documentação do [Next.js](https://nextjs.org/docs/pages/building-your-application/configuring/environment-variables#default-environment-variables):

>Good to know: `.env`, `.env.development`, and `.env.production` files **should be included in your repository as they define defaults.** `.env.local` should be added to `.gitignore`, as those files are intended to be ignored. `.env.local` is where secrets can be stored.

Ou seja, seguindo a documentação oficial do DotENV, não é recomendado fazer o commit do arquivo `.env`, no entanto para a documentação do Next.js, o indicado é exatamente fazer o commit de tal arquivo pois ele define os valores padrão.

O Next.js faz tal recomendação, pois você pode definir os valores padrões para cada tipo de ambiente através do nome do seu arquivo: `.env` para todos os ambientes, e `.env.development` para o ambiente de desenvolvimento. Lembrando que de acordo com o ambiente, um tem precedência sobre o outro, como o `.env.development` que em ambiente de desenvolvimento, sobrepõem o `.env`. Do mesmo jeito, se você injetar valores direto no `process.env`, tais valores teram precedência sobre qualquer outro. E isso é exatamente o que a Vercel faz pelo painel de Enviroment Variables.

## Credentials
**Credentials**, ou "credenciais", são informações utilizadas para permitir o acesso a serviços ou locais específicos, uma senha, por exemplo, é uma credencial. O nome de um banco de dados também pode ser classificado como uma credencial. Por serem dados delicados, tais informações não devem ser vazadas por questão de segurança. No entanto, muitas vezes precisamos informar a senha do banco de dados para se conectar ao mesmo, e como vimos no tópico anterior, colocamos essas credenciais no arquivo de ambiente. Dessa forma, se fizermos o commit desse arquivo, nossas credenciais podem ser vistas por qualquer um que acesse o repositório.

É por causa disso que devemos tomar atenção em relação as credenciais do nosso projeto. Não colocar as informações reais no `.env.development`, apenas as credenciais locais. No entanto, se as informmações forem vazadas no repositório, ainda tem maneiras de resolver isso.

---

- [Anterior](/dias/dia18.md) - [Próximo](/dias/dia20.md) - [Sumário](../README.md)
