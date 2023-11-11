# Fundamentos: HTTP e API (Dia 16)
No dia 16, exploramos assuntos essenciais ao desenvolvimento, desde tipos de testes automatizados, recomendo ver o [Testes Automatizados (Dia 15)](/dias/dia15.md) para entender melhor sobre testes, até protocolo **HTTP** e **API**, para mais informações sobre protocolo, recomendo ver o [Fundamentos: Protocolos (Dia 4)](/dias/dia04.md).

## HTTP

## API
**API** é um acrônimo de **Application Programming Interface**, ou em português "Interface de Programação de Aplicações". Para compreendermos o que de fato é uma **API**, precisamos esmiuçar melhor o seu nome e suas implicações. Vamos começar por **Interface**. Uma **interface** é um meio pela qual alguém **interage** com um dispositivo, ou seja, é o meio por onde um usuário e um dispositivo vão se comunicar.

Em seguida, temos **programming**, ou **programação**. Primeiramente, **programação** está relacionada ao ato de programar, que é elaborar um programa de computador realizando **implementações**. E dentro do contexto de **API**, o termo **programação** associa-se a algo programável. Quando comparamos uma interface voltada para seres humanos com uma **API**, a diferença é notoria, uma vez que interfaces web, por exemplo, possuem menus, estilizações, layouts, etc., enquanto uma **API** foca em apresentar suas informações de uma **meio** diferente, que é torne mais fácil de ser lido por um outro programa.

Por fim, temos **application**, ou **aplicações**. Uma **aplicação** é um programa ou até mesmo um conjunto de programas que é utilizado para realizar uma tarefa específica ou múltiplas tarefas relacionadas.

Em conclusão, **API** é uma interface voltada a apresentar uma aplicação de uma maneira que seja fácil a implementação ou integração da mesma com um outro programa.

## Tipos de Testes
No geral, existe 3 principais tipos de testes automatizados, sendo eles: **testes de unidade** ou **testes unitários** (_Unit Tests_), **testes de integração** (_Integration Tests_) e **testes de ponta a ponta** (_testes end-to-end_). Em resumo, os **testes de unidade** são os mais fáceis de serem feitos, e seu propósito está em testar um único elemento dentro do software, como métodos, funções individuais de classes, componentes ou módulos. Por causa de sua simplicidade, seu custo é baixo e são executados com maior rapidez.

Os **testes de integração**, por outro lado, possuem uma complexidade maior do que os de unidade, e seu foco está em testar a integração de diferentes módulos ou serviços usados pelo seu software, como a integração com o banco de dados, uma **API**, etc.

Por último, os **testes ponta a ponta** são dentre os 3, o mais complexo e com maior custo de execução. O objetivo desse tipo de teste é simular o comportamento de um usuário com o software em um ambiente de sistema completo, incluindo diversos fluxos, como carregamento de página, login, cenários de validação de e-mail, senha, etc.

Para saber mais sobre testes, veja [Tipos de testes: quais os principais e por que utilizá-los?](https://www.alura.com.br/artigos/tipos-de-testes-principais-por-que-utiliza-los).
