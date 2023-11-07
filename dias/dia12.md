# Registro de Domínio e Configuração de DNS (Dia 12)
O dia seguinte ao [Fundamentos: Domain Name System (Dia 11)](/dias/dia11.md), trata sobre a parte prática do DNS, desde o **registro do domínio** até a **configuração do servidor DNS**.

Além disso, durante a Pista Rápida, o Filipe fala sobre a **Bomba de Efeito Moral**, que é como ele prefere chamar a sensação de quando algo dá errado e você leva um choque pelo susto. A escolha de onde essa bomba vai explodir, está em nossas mãos, se preferimos que isso acontece em casa, sala de aula, no trabalho, etc.

## Registrando um Domínio
Quando vamos registrar um domínio, nós somos o **Registrant**, ou seja, "Registrante". A partir daí precisamos de algo que funcione como interface para realizar a reserva do seu domínio próprio domínio, para isso existe o **Registrar**, ou "Registrador". Alguns exemplos de registradores são: Registro.br, HostGator, UOL Host, Locaweb, dentre outros.

Quando você escolhe um nome de domínio, o registrador verifica se o mesmo está disponível ou não, através da lista dentre do **Registry**, ou "Registro". No caso do `.br`, o registro é o [NIC.br](https://nic.br/), que é um acrônimo de **Network Information Center**, ou “Centro de Informações sobre Rede”, que se refere aos centros responsáveis por publicar as tabelas com alocações de nomes e números IP.

Por fim, o próprio **Registry** vai atualizar o servidor TLD, que no caso do zona TLD `.br`, é gerenciado pelo [NIC.br](https://nic.br/).

## Configurando o servidor de DNS
Quando registramos um servidor, geralmente ele vai ter consigo um apotamento padrão para o servidor autoritativo. No caso do Registro.br, o DNS padrão é a.auto.dns.br e b.auto.dns.br. Para configurar o servidor DNS, é possível usar servidores da Cloudflare, Vercel, e outros que também fornecem esse tipo de serviço, seja pago ou gratuito.

No caso do curso.dev, usamos o serviço da Vercel e seus nameservers.

---

- [Anterior](/dias/dia11.md) - [Próximo](/dias/dia13.md) - [Sumário](../README.md)
