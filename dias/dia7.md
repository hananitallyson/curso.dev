# Fundamentos: Cliente e Servidor (Dia 7)
Chegou a hora de falarmos sobre **Cliente** e **Servidor**, além de outras coisas que estão presentes nas vídeo-aulas do dia 7.

Se essa não é a primeira vez que você mexe com desenvolvimento, já deve ter ouvido falar sobre **client** e **server**, ou respectivamente, cliente e servidor. Esses dois termos representam a dinâmica entre uma entidade que realiza pedidos (cliente) e outra que responde por esses pedidos (servidor).

Uma analogia para isso, é quando pedimos algo para um garçom, nessa situação nós somos o cliente e o garçom o servidor. No entanto, existe mais camadas nisso, quando por exemplo, fazemos nosso pedido ao garçom e ele faz o pedido à cozinha para preparar nossa comida. Em algo desse tipo, nós ainda somos o cliente, e o garçom ainda é o nosso servidor, mas o garçom também é um cliente, que agora está pedindo algo à cozinha que é outro servidor. Quando a comida está pronta, a cozinha entrega ao garçom, e ele nós entrega a comida que pedimos.

No [Fundamentos: Protocolos (Dia 4)](#fundamentos-protocolos-dia-4), aprendemos o que são protocolos. Esse conhecimento é fundamental, uma vez que a comunicação entre cliente e servidor, funciona através desses protocolos.

## Hosting
**Hosting**, do inglês, "Hospedagem", é o ato de hospedar um site. O termo hospedar é utilizado, pois a própria palavra significa oferecer ou receber abrigo, que nesse caso, é uma máquina que oferece abrigo para os arquivos do nosso projeto. E é através dela, que outros clientes, podem acessar o nosso site por essa máquina, que por sua vez, é um servidor dedicado para hospedagem.

### Deploy
**Deploy**, também vindo do inglês, significa "Implantar" ou "Depositar", sendo o termo utilizado para se referir a ação de colocar esses arquivos do nosso projeto dentro do servidor de hospedagem.

### Continuous Integration
**Continuous Integration** ou **Integração Contínua**, é uma prática que envolve a implementação contínua de novas funcionalidades/versões. Esse fluxo ocorre quando passamos nosso projeto para uma máquina chamada **continuous integretor** ou **C.I**, que realiza testes no nosso código. Se tudo estiver certo, ela envia para outra máquina dedica a **build**, e que em seguida, vai ser enviada de fato para um servidor que vai disponilizar o acesso ao projeto pela internet.

### Build
Esse processo, chamado de **build**, ou "construção", é realizado no código-fonte do projeto e serve para construir uma versão mais otimizada dele, que por sua vez pode rodar no servidor e ser aberta pelo navegadores. O processo de **building** envolve várias funções, como controle de versão, qualidade de código e compilação. Para saber mais, acesse o link abaixo.
- [Build](https://pt.wikipedia.org/wiki/Build)

## Evolução da Hospedagem
Na segunda vídeo-aula do dia 7, o Filipe conta como foi a evolução da hospedagem de sites, desde usar os próprio computador como **host** até o fluxo do **C.I** mencionado anteriormente.

Bem no começo da Internet, os sites eram hospedados em computadores pessoais, mas isso trazia vários problemas, principalmente, questões de segurança. Assim surgiu computadores dedicados a hospedagem, chamados de server, ou servidores, que serviam os sites para as pessoas. Com o passar do tempo, começou a ser visto complicadores nesse fluxo, como a questão de ficar precisando enviar arquivos para o servidor.

Foi aí que os desenvolvedores da época começaram a mexer nos arquivos, diretamente no servidor, seja através do Windows Server ou SSH do Linux. Mas isso é praticamente um passa para trás, e muitas vezes, ficava complicado sincronizar os arquivos do servidor, com os computadores pessoais dos desenvolvedores. Mas, com a chegada do git, isso mudou!

A ideia foi colocar o git também no servidor, dessa forma, os desenvolvedores davam `push` no repositório, enquanto o servidor realizava o `pull` do mesmo. Assim, se tornava mais fácil toda essa questão de manter o servidor sincronizado com as novas alterações. Com a chegada desse fluxo, automatizações começaram a surgir e em um momento a frente, o fluxo do continuous integration chegou.

## Princípio do Privilégio Mínimo
Na terceira vídeo-aula da pista lenta, o Filipe menciona o "Principle of Least Privilege", ou Princípio do Privilégio Mínimo, em português. Esse princípio define que, por questões de segurança de sistema, é ideal que seja atribuido a menor quantidade de acessos, credenciais ou privilégios para uma conta dentro do sistema. Afinal, qualquer coisa pode ser considerada uma entrada para ataques.