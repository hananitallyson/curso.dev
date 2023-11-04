# Fundamentos: Domain Name System (Dia 11)
**Domain Name System** ou **DNS** é um sistema que associa nomes aos endereços IPs correspondentes. O [DNS](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name) é um sistema hierárquico e distribuído que funciona como uma lista telefônica que associa números a um nome.

Na primeira aula da pista lenta, o Filipe afirma que os domínios são uma mentira, e de fato são. Os domínios nada mais são do que apelidos para um conjunto de números que chamamos de **endereço IP**, que já foi mencionado em [Fundamentos: Protocolos (Dia 4)](/dias/dia4.md#internet-protocol).

Quando acessamos um domínio no nosso navegador, na realidade estamos fazendo uma **requisição à um servidor DNS**, que por sua vez recebe esse "apelido" e **verifica** se há alguma associação ao mesmo. Se houver uma associação do domínio à um endereço IP, então o DNS **devolve** esse endereço para nós, e então **acessamos** o servidor final que queriamos. É por causa desse processo que geralmente fazemos a analogia do DNS com a lista telefônica.

Eu gostaria de enfatizar a ordem mecânica desse processo, assim como o Deschamps enfatizou na vídeo-aula. Mecanicamente falando, primeiro o nosso dispositivo faz a requisição, depois o servidor DNS faz a busca pelo endereço e então devolve para o nosso dispositivo, e agora o nosso dispositivo acessa o servidor final. Ou seja, em nenhum momento o servidor DNS entrou em contato com o servidor final, como mostrado abaixo.
```

Servidor DNS <-----> Dispositivo -----> Servidor Final

```
Mas claro que isso é apenas uma exemplificação, a estrutura relacionada ao DNS na verdade é ainda mais complexa. Passamos pelo **Recursive Resolver** ou **Recursive DNS Server** no nosso provedor de internet, depois pelo **Root Servers**, seguidos dos **TLDs Servers**, então vem o **Authoritative Server**, para que no fim o IP chegue no **Recursive Resolver** e ele possa devolver para nosso dispositivo.
```
                    Root Server
                        ^
                        |
                        ˇ
TLD Server <--> Recursive Resolver <-----> Dispositivo -----> Servidor Final
                        ^
                        |
                        ˇ
               Authoritative Server
```

## Recursive Resolver / Recursive DNS Server
O Recursive Resolver é aquele que obtém a requisição do usuário. Em seguida, ele pergunta ao **Root Server** sobre a localização do servidor **TLD** (Top-Level Domain). O Recursive Resolver então consulta o servidor **TLD** para obter informações sobre qual é o **Authoritative Server** responsável pelo domínio específico desejado. Esse processo é um vai e volta, onde o Recursive Resolver sai buscando pelo endereço associado ao domínio.

## Root Server
O Root Server tem como função, ler o domínio de trás para frente, com o intuito de identificar qual a **TLD** do domínio. No entanto, essa não é a primeira coisa que o Root Server identifica. O **Fully Qualified Domain Name** ou **FQDN** é o endereço completo de um host ou computador da internet. Ele fornece sua localização exata no DNS, especificando o nome do host, o domínio e o TLD.

Por exemplo, no domínio `domain.net`, seu Fully Qualified Domain Name seria `domain.net.` com um ponto no final. Isso indica o **Root Domain**. Seguindo de trás para frente, temos o TLD, que nesse caso é `.net`. Uma vez identificado o TLD, o Root Server indica ao Recursive Resolver onde está o TLD Server correspondente.

## TLDs Servers
Depois de receber a lista de servidores TLD correspondente do Root Server, o Recursive Resolver então parte para buscar o IP nos TLDs Servers. No nosso exemplo, o TLD Server seria o **TLD .net**, que é uma **gTLDs**, ou **Generic Top-Level Domains**, ou seja, uma TLD genérica. Existe também as **ccTLDs**, que são TLDs associadas à um país, como o `.br` do Brasil.

O TLD Server verifica o domínio que lhe foi passado e indica qual o **Authoritative Server** correspondente para o Recursive Resolver.

## Authoritative Server
É aqui no Authoritative Server, onde fica todos os registros, ou **DNS Records**, do domínio. O Authoritative Server recebe o domínio e devolve, finalmente, o endereço IP correspondente ao servidor final para o Recursive Resolver.

## Time To Live (TTL) e Cache
**Time To Live** é uma estratégia para tornar todo esse processo de DNS algo mais viável. O TTL é um indicador de quanto tempo um registro deve ser mantido em cache, ou seja, o seu tempo de vida, que é a própria tradução do termo Time To Live.

---

- [Anterior](/dias/dia10.md) - [Próximo](/dias/dia12.md) - [Sumário](../README.md)
