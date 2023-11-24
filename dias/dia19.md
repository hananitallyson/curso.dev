# Absolute Imports, Services Scripts, ENV e Credentials
## Absolute Imports


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
