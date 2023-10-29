# Fundamentos: Git (Dia 5)
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
Outra maneira de realizar o commit é adicionando a flag `-m` para escrever a mensagem de commit direto da linha de comando:
```shell
git commit -m "<mensagem>"
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
Mas como eu mencionei no começo dessa parte sobre amend, ainda existe efeitos colaterais na linha do tempo, e quando realizamos o amend, o identificador do commit é alterado. Esse identificador pode ser visto através do comando já apresentado `git log`, no entanto, para ver melhor só essas informações de cabeçalho, use a flag `--oneline` para mostrar cada commit em uma única linha no terminal.
```shell
git log --oneline
```
Isso acontece, pois os commits são imutáveis, ou seja, não podem ser de fato alterados, eles são únicos!

## .gitignore
Lembra que no final do dia 4 eu disse que o Vercel havia indicado que o arquivo `.next` não deveria ser enviado dentro do repositório, e que era importante lembrar disso? Bem, aqui vai o motivo!

Quando criamos um repositório git para nosso projeto, geralmente vai acabar existindo pastas e arquivos que nós não queremos que vá junto do projeto, seja por organização ou por segurança. Um exemplo disso, é o arquivo `.env` que deve ser ignorado pelo git por motivos de segurança, uma vez que esse arquivo pode conter informações sobre banco de dados, chaves de API ou configurações gerais da aplicação, que poderiam facilmente serem usadas em um ataque. Por causa disso, existe o arquivo de texto `.gitignore`, que serve basicamente para dizer ao git quais arquivos e pastas devem ser ignorados.

Para fazer isso, basta criar o arquivo com o nome `.gitignore` e colocar o nome dos arquivos e pastas, faça o commit e pronto.

---

- [Anterior](/dias/dia4.md) - [Próximo](/dias/dia6.md) - [Sumário](../README.md)
