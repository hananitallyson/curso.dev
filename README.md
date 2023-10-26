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

Além dessa explicação maravilhosa, o Deschamps também explica o que é um repositório e como criar um na plataforma do GitHub, e aproveitando o gancho, fala sobre uma estratégia de SEO para que o seu repositório seja encontrado com mais facilidade através das ferramentas de busca.

A última aula tratou sobre ambiente de desenvolvimento, e entramos no entendimento sobre os conceitos de **Função** e **Estética**. A ideia é que todas as ferramentas (linguagens, sistema operacional, IDE, etc.) possuem dois lados, a parte de sua **função** que está atrelada ao que ela pode lhe oferecer de forma produtiva, e a **estética** que seriam as coisas que lhe agradam ou não, e que estão atreladas a como a ferramenta se apresenta. Ele pontua muito bem que a **estética** depende do gosto pessoal, e por causa disso, cada um tem sua opinião em relação a determinada ferramenta.

Eu não pude deixar de me lembrar dos vídeos do [Fabio Akita](https://www.youtube.com/@Akitando/), onde ele fala sobre **"Sua Linguagem NÃO É Especial!"** e como ficar de clubismo com uma linguagem, sistema operacional ou seja o que for, não vai te levar muito longe. Abaixo deixarei os links para os vídeos em que ele aborda esse assunto.
- [Sua Linguagem NÃO É Especial! (Parte 1)](https://youtu.be/p9-WuJbVHHc)
- [Sua Linguagem NÃO É Especial! (Parte 2)](https://youtu.be/XcTTajFENHI)
- [Sua Linguagem É Especial? Parte 1 em 2001](https://youtu.be/NwAvovzHRDU)
- [Sua Linguagem É Especial? Parte 2 em 2001](https://youtu.be/O4CWVQLbi48)

# Dia 3
O terceiro dia já começa com uma frase do Carl Sagan:
> Se você quiser fazer uma torta de maçã a partir do zero, você deve primeiro inventar o Universo.

A partir dessa frase, começamos a tratar sobre como hoje **nada mais é criado do zero**, principalmente, no ramo da tecnologia. Nós programamos em uma linguagem, que provavelmente, não foi você que a criou, além disso, usamos frameworks e outros módulos que, de outra vez, provavelmente não foi criado por você. Criamos em cima de coisas que já foram criadas, e assim podemos chegar em novos patamares.

Além dessa reflexão, também há a parte técnica das aulas, onde deixamos o nosso projeto `clone-tabnews` nas mesmas versões de NodeJS, Next.JS, React e React-dom. Inclusive, eu comento, na vídeo-aula sobre NodeJS e NVM, o uso de outro gerenciador de versões que não é somente para o NodeJS, mas para várias linguagens: o **asdf**.

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

# Dia 4
A primeira vídeo-aula da pista lenta fala sobre [protocolos](https://pt.wikipedia.org/wiki/Protocolo_(ci%C3%AAncia_da_computa%C3%A7%C3%A3o)) e o que eles são. O exemplo citado na aula, foi o telefone sem fim, que de fato é uma boa analogia ao esquema de protocolos dentro da Web. Em resumo, protocolos são regras para comunicação que foi acordada entre duas ou mais partes, essas regras vão definir como enviar e receber informações.

Além disso, colocamos também o servidor local para rodar, junto com nosso projeto `clone-tabnews`. Nesse processo, o Filipe fala sobre a organização de páginas do Next que é **File-Based Routing**, ou seja, **Roteamento Baseado em Arquivos**. E aproveitando o gancho, ele também fala como surgiu a ideia por trás das páginas Index, que comumente, é a página inicial da maioria dos sites.

## UDP e TCP
Dentre os protocolos citados na aula, estão os dois: UDP e TCP. **User Datagram Protocol** e **Transmission Control Protocol**. Esses dois são os principais protocolos de gerenciamento de pacotes da Internet, no entanto, o uso deles depende do objetivo a ser alcançado. Se formos comparar a segurança de dados, em relação a perda de pacotes, o TCP é superior, pois possui uma verificação para garantir que todos os pacotes foram recebidos corretamente. Enquanto isso, o UDP não garante essa segurança. No entanto, tudo tem seu preço! O TCP, por causa dessa garantia, demanda mais tempo.

O UDP, por sua vez, é mais rápido e por causa disso é geralmente utilizado por serviços como **transmissões ao vivo** e **vídeo-games**. Já que nesse cenário, a perda de pacote é irrisória e pode ser compensada pelos próprios usuários, como quando pedimos para alguém repetir o que disse, pois a chamada havia "travado". No mundo dos jogos, chamamos essa perda de pacotes de **Lag**. Para saber mais sobre isso, veja o vídeo compartilhado pelo próprio Filipe: [HTML5 Games - UDP vs TCP](https://youtu.be/ZEEBsq3eQmg).

## Desafio
No fim do dia, o Filipe manda um desafio: colocar o projeto em um link público e enviar esse link para alguém, e então ver qual é a reação dela para a mensagem deixada na página.

Eu resolvi fazer esse desafio mandando o link para o meu melhor amigo, então a mensagem que deixei na página era para ele. Depois, eu precisava encarar a ideia principal do desafio, colocar o projeto no ar!

Para isso, eu usei o Vercel. Eu cheguei nessa conclusão, pois em aulas anteriores, o próprio Deschamps já havia mencionado que era possível hospedar de forma gratuita no Vercel, sendo assim, fiz o **commit** através do `git` para o repositório no GitHub. De lá, o Vercel fez o resto, configurei poucas coisas e pronto, o site estava no ar: [https://hananitallyson-clone-tabnews.vercel.app/](https://hananitallyson-clone-tabnews.vercel.app/).

É interessante mencionar que durante o deploy, o Vercel indicou que o arquivo `.next` não deveria ser enviado dentro do repositório. No dia seguinte, isso vai ser importante...

# Dia 5
Agora o papo é sobre [Git](https://git-scm.com/). Como eu acabei de dizer, o dia 5 foi focado em compreender mais sobre o **Git** e **Versionamento de Código**. Mas afinal, o que são essas coisas?

Bem, começando pelo Git, ele é uma ferramenta para **Versionamento de Cógido** que funciona de forma **distribuída**, ao invés de **centralizada** como outros versionadores.

Versionamento de Cógido é quando organizamos as **versões** do nosso código, para ficar mais fácil de acessar informações de Como?, Quando?, E quais são as modificações?. E a melhor forma de fazer isso, atualmente, é através do Git.

## Como era antes do Git?
Na aula, o Deschamps fala sobre como era antes da criação do Git, e menciona como antes os versionadores eram **centralizados**. Isso significa que existia uma cópia principal do repositório e as pessoas reservavam o acesso delas a essa cópia, em um sistema de **Checkout** e **Check-in**. Dessa forma, o código ficava inacessível a alterações para outros enquanto a pessoa não realizasse o check-in da sua cópia modificada, ou seja, era uma maneira de "alugar" os arquivos do projeto.

Novamente, enquanto eu assistia essa vídeo-aula, lembre-me de que o [Fabio Akita](https://www.youtube.com/@Akitando/) já havia postado um vídeo falando sobre Git. Segue o link para o vídeo abaixo:
- [Entendendo GIT | (não é um tutorial!)](https://youtu.be/6Czd1Yetaac)

## Git Log (e o Jogo dos 7 Erros)
"Git Log (e o Jogo dos 7 Erros)" foi o título da segunda vídeo-aula da pista lenta. Nesse video o Filipe fala sobre diversos conceitos que são importantes para compreender Git, como: **diff**, **blob**, **log** e **commit**.

### Diff
De forma bem simples, `diff` é a abreviação da palavra "Difference", que do inglês significa "Diferença". Esse termo é um utilitário que permite comparar dois arquivos linha por linha. Ou seja, é um comando que compara arquivos e devolve a diferença entre eles.

Em Linux podemos usar o `diff` da seguinte forma:
```shell
diff <arquivo1> <arquivo2>
```
Aqui estamos comparando o `arquivo1` com o `arquivo2`. O resultado disso será a diferença entre os dois arquivos, sendo informado se algo foi removido ou adicionado entre o `arquivo1` e o `arquivo2`.

### BLOB
BLOB é um acrônimo para **Binary Large OBject** ou também **Basic Large OBject**. Basicamente, blob é um conjunto de dados binários que são armazenados em uma única ententidade em um sistema de gerenciamento de bancos de dados.

No git, o blob é a união entre o conteúdo de um arquivo e seu identificador, sendo armazenado no diretório oculto `.git`. A partir disso, o git guarda as versões dos arquivos, e quando uma nova versão é inserida, ele cria um novo blob somente para os arquivos modificados. Aqueles que não sofreram alteração são apontados para sua versão anterior, já que permanecem iguais. Dessa forma, um projeto com dois arquivos vão possuir dois blobs, um para cada. Se alterarmos o primeiro e deixamos o segundo igual nessa nova versão, o git vai criar um novo blob para o primeiro arquivo e vai apontar o blob do segundo arquivo da versão anterior dentro dessa nova versão.

Quando eu menciono "versão", eu estou me referindo a um **commit**, isso vai ficar mais claro na parte seguinte.

### Log e Commit
"Log" significa "Registro" em inglês, e dentro do git, é a representação de todos os registros realizados no `.git`. Para acessar esse registro use o seguinte comando dentro de um diretório onde o git já tenha sido inicializado:
```shell
git log
```
O resultado desse comando deve ser o registro de seus **commits** com informações sobre autor e data, dentre outras coisas.

Agora, o que é commit? Bem, commit é o termo técnico usado para se referir ao que na explicação sobre blob eu usei a palavra "versão". Um dos significados dessa palavra é "compromisso", e também vem do inglês. A ideia é que um commit seria um compromisso do autor em relação aquelas modificações de seu código dentro do projeto. Então, quando realizamos a operação de commit, estamos enviando as últimas alterações do código fonte para o seu respectivo repositório.

Antes que um commit seja realizado é importante que as modificações tenham sido adicionadas. Usamos o `add` para isso.
```shell
git add .
```
O ponto representa que estamos adicionando todos os arquivos. Então podemos seguir para o commit através do seguinte comando:
```shell
git commit
```

## Stage
Na terceira aula da pista lenta, aprendemos sobre os **stages** em que um arquivo passa dentro do git. "Stage" vem do inglês e significa "Estágio", e dentro do git existe 3 estágios para os arquivos: **modified**, **staged** e **committed**. Esses 3 estágios representam, respectivamente, os estágios de modificado, arranjado (ou planejado) e compromissado (ou cumprido). Os estágios mencionados funcionam como uma "escada", onde o primeiro degrau é o modified, o seguinte é staged, e por fim o committed.

No entanto, antes de um arquivo se tornar modified, ele na realidade estará em um estágio "não catalogado" podemos assim dizer... O termo correto para esse pseudo-estágio é **untracked**, ou seja, não rastreado.

Uma boa analogia para entender todo esse processo dos 3 esátgios, é imaginar que o nosso projeto é um show, com os bastidores e o palco. Quando modificamos um arquivo, esse está nos bastidores do show. Ao adicionarmos ele através do `git add` estamos colocando o arquivo no palco, que em inglês, o termo para palco é "Stage". Então, quando a "apresentação" termina, o show foi concluído com sucesso, sendo assim ele foi cumprido, ou seja, committed.

Para compararmos o que está fora e dentro do git, usamos o comando:
```shell
git status
```

## Amend
A última aula desse longo dia 5, foi dedicada a falar sobre viagem no tempo dentro do git, ou melhor dizendo, falar sobre **Amend**! Esse termo do inglês, em português, significa "Emendar", ou seja, alterar ou remendar algo. Por isso a brincadeira com viagem no tempo, pois, o amend do git nos permite alterar um commit, como se desde o começo, ele sempre tivesse sido daquela forma... Apesar de ainda existir certos efeitos colaterais na linha do tempo.

Para continuarmos com o entendimento do amend, precisamos colocar nas nossas cabeças de que existe dois espaços em que o nosso projeto está presente. Um é o **Working Directory**, ou "pasta de trabalho", que é a pasta do próprio projeto. E outro espaço é o repositório, guardado dentro do `.git` que também fica na pasta do projeto. Isso torna possível compararmos a nossa versão atual com a versão anterior guardada no repositório, através do comando:
```shell
git diff
```
Novamente, a palavra **diff** aparece, e dessa vez sabemos que isso significa que estamos comparando versões, e que queremos ver qual a diferença entre elas.

Agora, para que serve o **Amend**? Bem, quando fazemos um commit, mas queremos modificar novamente aquele arquivo, mas sem precisar criar um "novo", então podemos usar a **flag** `--amend` junto do comando de commit. As **flags** servem para alterar ou modificar o comportamente de um comando, e nesse caso, vai modificar o commit para que ele "volte no tempo" e altere o commit anterior que está guardado dentro do repositório.
```shell
git commit --amend
```

### Imutabilidade
Mas como eu mencionei no começo dessa parte, ainda existe efeitos colaterais na linha do tempo, e quando realizamos o amend, o identificador do commit é alterado. Esse identificador pode ser visto através do comando já apresentado `git log`, no entanto, para ver melhor só essas informações de cabeçalho, use a flag `--oneline` para mostrar cada commit em uma única linha no terminal.
```shell
git log --oneline
```
Isso acontece, pois os commits são imutáveis, ou seja, não podem ser de fato alterados, eles são únicos!
