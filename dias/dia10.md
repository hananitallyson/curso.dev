# Estilização de Código (Dia 10)
Esse dia começou com um experiência de vida contada pelo Filipe Deschamps da época que ele desenvolvia no projeto **pagar.me**. Em resumo, essa experiência o levou a entender a importância da organização de um código, ou para ser mais exato, a **estilização** do mesmo.

Assim como na escrita a mão cada pessoa possui o seu jeito próprio de escrever, durante o desenvolvimento não seria diferente. Cada desenvolvedor possui sua própria maneira de escrever um código, com ou sem ponto e vírgula, com 2 ou 4 espaços no tab, entre várias outras coisas que marca o traço daquele desenvolvedor no código do projeto. Se você está desenvolvendo sozinho, você pode seguir a formatação que desejar, no entanto, quando colocamos mais pessoas nisso, podemos começar a ter problemas.

Imagine a seguinte situação: 10 pessoas trabalhando no mesmo projeto e cada uma tem um estilo diferente de formatação. No fim do dia, quando vamos ver o código do projeto, está tudo bagunçado, uma parte do código tem `;`, outros não. Outras partes estão com uma indentação de 4 espaços no tab, outras partes com 8 espaços... Acho que já deu para notar que isso acaba causando uma confusão enorme, e quando se trata de projetos que visam a escalabilidade, ou seja, ter a capacidade de crescer, é necessário criar um padrão para todo o projeto.

Dessa forma chegamos nas duas tecnologias indicadas pelo Filipe: [EditorConfig](https://editorconfig.org/) e [Prettier](https://prettier.io/). Se seguirmos as documentações, chegaremos ao resultado satisfatório de configuração.

Além de tudo isso, esse dia também teve partes práticas. Configuramos essas duas tecnologias, e inclusive instalamos algo a mais ao nosso projeto. Também criamos novos scripts no `package.json`:
```json
"lint:check": "prettier --check .",
"lint:fix": "prettier --write ."
```
O script `lint:check` serve para verificar os arquivos do projeto, para procurar algum em que o Prettier não tenha feito a estilização. Enquanto isso, o `lint:fix` serve exatamente para executar o Prettier.

---

- [Anterior](/dias/dia9.md) - [Próximo](/dias/dia11.md) - [Sumário](../README.md)
