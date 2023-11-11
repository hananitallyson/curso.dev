# Git: Respositório Local e Remoto (Dia 6)
Continuando essa saga com o git, nas aulas do dia 6, o Filipe fala mais sobre **repositório remoto** e os assuntos que cercam isso. 

Para começarmos, a primeira vídeo-aula da pista lenta trata sobre **push**, que em inglês significa, literalmente, "Empurrar". Quando realizamos o commit no nosso projeto, aplicamos as alterações diretamente em uma nova versão que fica salva no repositório **local**, no entanto, muitas vezes queremos compartilhar nosso código, ou salvar ele em algum lugar fora da nossa máquina. Para isso, precisamos mandar o nosso **repositório local** para um **repositório remoto**, a **origin**. O comando que usamos para enviar os arquivos ao repositório remoto é o seguinte:
```shell
git push
```

Para ver quais servidores remotos temos configurados usamos o comando a seguir:
```shell
git remote
```
Ao executar, você provavelmente verá o nome origin como output do comando, isso caso tenha clonado seu repositório. Para saber ainda mais sobre, acesse o link abaixo.
- [Fundamentos de Git - Trabalhando de Forma Remota](https://git-scm.com/book/pt-br/v2/Fundamentos-de-Git-Trabalhando-de-Forma-Remota)

## Branch
Apesar de o foco não ser Branches nesse aula, o Deschamps explica bem por cima, que a branch em que estamos trabalhando é a **main**, ou seja, a branch principal. É possível ver isso através dos repositórios, que indicam *local/main** e **origin/main**, ou seja, primeiro o repositório e em seguida a branch trabalhada. Para ver qual a branch estamos trabalhando, use o comando:
```shell
git branch
```

## Pushing e Pulling
Um dos principais objetivos quando trabalhamos com git é de facilitar a nossa vida quando queremos "puxar" alterações do código do remoto para o local, assim como "empurrar" as alterações que fizemos. Nessa situação de enviar nossas alterações, já sabemos qual comando usar, o `git push`, mas para fazer o download do repositório, ou seja, baixar as alterações, como fazemos? Bem, a resposta está no **pull**, que em inglês significa, literalmente, "puxar".
```shell
git pull
```

## Forçando um Push
Vamos dizer que eu realizei um commit de algo errado no cógido, e sem perceber o erro, eu mandei isso para o repositório remoto usado o `git push`. Bem, tudo que eu preciso fazer é usar o conhecimento que adquirimos na aula do dia anterior, e "viajar no tempo" através da flag `--amend` do comando `git commit`, modificar a linha do tempo do meu repositório e dar `git push` novamente, certo? Não!

Se você fizer esse teste no seu projeto, vai perceber que o git vai retornar uma mensagem de erro, indicando que o seu push foi rejeitado! Isso acontece pois agora existe uma disparidade entre o **local/main** e a **origin/main**. O commit do local é diferente do que está na origin, e ambos estão indicando o commit anterior. Segue o exemplo:
```
(Origin) Commit A <-- Commit B1
(Local)  Commit A <-- Commit B2
```
O commit B1 é aquele com o erro, e o commit B2 foi o realizado com `--amend`. Perceba que existe uma divergência entre as linhas do tempo, e por causa disso, o git recusa o seu novo `git push`. No entanto, existe uma forma de **forçar** isso, usando a flag `--force` ao comando de push.
```shell
git push --force
```
Ou sua versão comprimida:
```shell
git push -f
```
Apesar de ser possível, forçar um push não é indicado. É um comando periculoso e deve ser feito apenas em ocasiões de grande especificidade, e quando você ou sua equipe possuem total consciência da situação e de como isso vai afetar o projeto.

---

- [Anterior](/dias/dia05.md) - [Próximo](/dias/dia07.md) - [Sumário](../README.md)
