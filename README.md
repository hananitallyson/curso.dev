# curso.dev
Aqui, vou registrar minhas anotações relevantes ao [curso.dev](https://curso.dev/) como uma maneira de manter esse conhecimento anotado e disponível, servindo como uma motivação para eu pesquisar sobre os assuntos ministrados nas aulas e ir mais além!

Outro repositório meu que possui uma finalidade semelhante é o [Hanani's Guide to Front-end](https://github.com/hananitallyson/guide-to-front-end), onde eu reúno links de sites, artigos e vídeos sobre assuntos relacionados ao desenvolvimento Front-end.

# Dia 1
Dentro do curso, o dia 1 foi separado para dar boas-vindas aos alunos e para apresentar a organização do próprio curso. O curso.dev é dividido de uma maneira na qual os **alunos** são estimulados, e os **conteúdos** bem organizados. Todos os conteúdos dentro do curso são separados por dias, dessa forma, ao ver todas as vídeo-aulas e realizar os exercícios do dia, então aquele dia foi concluído. Como o próprio Deschamps menciona, esse ritmo que leva em consideração o dia é chamado de [Ritmo Circadiano](https://pt.wikipedia.org/wiki/Ritmo_circadiano).

## Pista Lenta e Pista Rápida
Todos os dias seguintes possuem a seguinte organização: conteúdos detalhados na **Pista Lenta** e um único vídeo que resume tudo, que é a **Pista Rápida**.

O aluno [André Cruz Mendes](https://github.com/andrecruzmendes) comentou no vídeo de explicação das pistas:
>Se você chegou agora no curso, vai encontrar as pistas rápidas no início de cada dia, mas na prática elas são produzidas e liberadas após as pistas lentas. Elas identificam os pontos mais importantes do conteúdo do dia e servem como um resumo do que foi ensinado em todas as lições (ou do que será ensinado, se você estiver assistindo antes). A dica, então, para aproveitar bem o conteúdo, é assistir a pista rápida antes e também depois, como uma forma de revisão.

Assim como ele, eu vejo essa sendo a melhor forma de absorver o conteúdo do curso, além de ser bem útil quando estamos querendo apenas um resumo sobre o assunto, apenas para fazer breves anotações ou para relembrar de certas coisas.

# Dia 2
Já no segundo dia, o Filipe Deschamps explica de uma maneira simples de entender o que é GitHub e qual a diferença entre GitHub e Git, comparando-o com o YouTube. Como foi dito na aula:
> [...] o Github é um YouTube, só que ele não hospeda vídeos, ele hospeda repositórios git. [...] Você pode fazer o upload desse repositório lá para o Github, com isso outras pessoas podem acessar e baixar esse repositório, podem deixar comentários, ou até coisas mais avançadas como enviar alterações de código...

Além dessa explicação maravilhosa, o Deschamps também explicar o que é um repositório e como criar um na plataforma do GitHub, e aproveitando o gancho, explica também uma estratégia de SEO para que o seu repositório seja encontrado com mais facilidade através das ferramentas de busca.

A última aula tratou sobre ambiente de desenvolvimento, e entramos no entendimento sobre os conceitos de **Função** e **Estética**. A ideia é que todas as ferramentas (linguagens, sistema operacional, IDE, etc.) possuem dois lados, a parte de sua **função** que está atrelada ao que ela pode lhe oferecer de forma produtiva, e a **estética** que seriam as coisas que lhe agradam ou não que estão atreladas a como a ferramenta se apresenta.

Eu não pude deixar de me lembrar dos vídeos do [Fabio Akita](https://www.youtube.com/@Akitando/), onde ele fala sobre **"Sua Linguagem NÃO É Especial!"** Abaixo deixarei os links para os vídeos em que ele aborda essa assunto.
- [Sua Linguagem NÃO É Especial! (Parte 1)](https://youtu.be/p9-WuJbVHHc)
- [Sua Linguagem NÃO É Especial! (Parte 2)](https://youtu.be/XcTTajFENHI)
- [Sua Linguagem É Especial? Parte 1 em 2001](https://youtu.be/NwAvovzHRDU)
- [Sua Linguagem É Especial? Parte 2 em 2001](https://youtu.be/O4CWVQLbi48)

# Dia 3
O terceiro dia já começa com uma frase do Carl Sagan:
> Se você quiser fazer uma torta de maçã a partir do zero, você deve primeiro inventar o Universo.

A partir dessa frase, começamos a tratar sobre como hoje **nada mais é criado do zero**, principalmente, no ramo da tecnologia. Nós programamos em uma linguagem, que provavelmente, não foi você que a criou, além disso, usamo frameworks e outros módulos que, de outra vez, provavelmente não foi criado por você. Criamos em cima de coisas que já foram criadas, e assim podemos chegar em novos patamares.

Além dessa reflexão, também há a parte técnica das aulas, onde deixamos o nosso projeto `clone-tabnews` nas mesmas versões de NodeJS, Next.JS, React e React-dom. Inclusive, eu comento na vídeo aula sobre NodeJS e NVM, o uso de outro gerenciador de versões para linguagens: o **asdf**.

## Gerenciador de Versão
Fica a recomendação do [asdf](https://asdf-vm.com/guide/getting-started.html), o gerenciador de versão para diferentes linguagens de programação, em que você adiciona plugins ao gerenciador, e através disso o asdf instala as versões. Além disso, é possível definir uma versão global e local para projetos naquela linguagem através dos comandos:
```shell
asdf global <nome> <versão>
```
```shell
asdf local <nome> <versão>
```

## Analysis Paralysis
Na última vídeo-aula do dia 3, o Deschamps traz o conhecimento sobre [Analysis Paralysis](https://en.wikipedia.org/wiki/Analysis_paralysis), que de acordo com a Wiki representa o estado de ficar paralisado por pensar demais. Ou seja, é o fenômeno que ocorre com muitos de nós quando pensamos demais sobre qual linguagem usar, ou qual framework devemos utilizar, e acabamos estagnados por causa da incerteza.
