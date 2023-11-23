# Absolute Imports, Services Scripts e ENV
## Absolute Imports
## Scripts
## Fazer Commit do .env é correto?
De acordo com a documentação oficial do [dotenv](https://nextjs.org/docs/pages/building-your-application/configuring/environment-variables#default-environment-variables):
>**No. We strongly recommend against committing your .env file to version control.** It should only include environment-specific values such as database passwords or API keys. Your production database should have a different password than your development database.

Enquanto na documentação do [Next.js](https://nextjs.org/docs/pages/building-your-application/configuring/environment-variables#default-environment-variables):

>Good to know: `.env`, `.env.development`, and `.env.production` files **should be included in your repository as they define defaults.** `.env.local` should be added to `.gitignore`, as those files are intended to be ignored. `.env.local` is where secrets can be stored.

Ou seja, seguindo a documentação oficial do dotenv, não é recomendado fazer o commit do arquivo `.env`, no entanto para a documentação do Next.js, o indicado é exatamente fazer o commit de tal arquivo pois ele define os valores padrão.

O Next.js faz tal recomendação, pois você pode definir os valores padrões para cada tipo de ambiente através do nome do seu arquivo: `.env` para todos os ambientes, e `.env.development` para o ambiente de desenvolvimento. Lembrando que de acordo com o ambiente, um tem precedência sobre o outro, como o `.env.development` que em ambiente de desenvolvimento, sobrepõem o `.env`. Do mesmo jeito, se você injetar valores direto no `process.env`, tais valores teram precedência sobre qualquer outro. E isso é exatamente o que a Vercel faz pelo painel de Enviroment Variables.
