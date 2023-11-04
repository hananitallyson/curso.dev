# Fundamentos: Domain Name System (Dia 11)
**Domain Name System** ou **DNS** é um sistema que associa nomes aos endereços IPs correspondentes. O [DNS](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name) é um sistema hierárquico e distribuído que funciona como uma lista telefônica que associa números a um nome.

Na primeira aula da pista lenta, o Filipe afirma que os domínios são uma mentira, e de fato são. Os domínios nada mais são do que apelidos para um conjunto de números que chamamos de **endereço IP**, que já foi mencionado em [Fundamentos: Protocolos (Dia 4)](/dias/dia4.md#internet-protocol).

Quando acessamos um domínio no nosso navegador, na realidade estamos fazendo uma **requisição à um servidor DNS**, que por sua vez recebe esse "apelido" e **verifica** se há alguma associação ao mesmo. Se houver uma associação do domínio à um endereço IP, então o DNS **devolve** esse endereço para nós, e então **acessamos** o servidor final que queriamos. É por causa desse processo que geralmente fazemos a analogia do DNS com a lista telefônica.

Eu gostaria de enfatizar a ordem mecânica desse processo, assim como o Deschamps enfatizou na vídeo-aula. Mecanicamente falando, primeiro o nosso dispositivo faz a requisição, depois o servidor DNS faz a busca pelo endereço e então devolve para o nosso dispositivo, e agora o nosso dispositivo acessa o servidor final. Ou seja, em nenhum momento o servidor DNS entrou em contato com o servidor final, como mostrado abaixo.
```

Servidor DNS <-----> Dispositivo -----> Servidor Final

```
Mas claro que isso é apenas uma exemplificação, a estrutura relacionada ao DNS na verdade é ainda mais complexa. Passamos pelo **Recursive Resolver** ou **Recursive DNS Server** no nosso provedor de internet, depois pelo **Root Servers**, seguidos dos **TLDs Servers**, então vem o **Authoritative Server**, para que no fim o IP chegue no **Recursive Resolver** e ele possa devolver para nosso dispositivo.

---

- [Anterior](/dias/dia9.md) - [Próximo](/dias/dia11.md) - [Sumário](../README.md)
