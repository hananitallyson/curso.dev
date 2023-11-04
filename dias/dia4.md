# Fundamentos: Protocolos (Dia 4)
A primeira vídeo-aula da pista lenta fala sobre [protocolos](https://pt.wikipedia.org/wiki/Protocolo_(ci%C3%AAncia_da_computa%C3%A7%C3%A3o)) e o que eles são. O exemplo citado na aula, foi o telefone sem fim, que de fato é uma boa analogia ao esquema de protocolos dentro da Web. Em resumo, protocolos são regras para comunicação que foi acordada entre duas ou mais partes, essas regras vão definir como enviar e receber informações.

Além disso, colocamos também o servidor local para rodar, junto com nosso projeto `clone-tabnews`. Nesse processo, o Filipe fala sobre a organização de páginas do Next que é **File-Based Routing**, ou seja, **Roteamento Baseado em Arquivos**. E aproveitando o gancho, ele também fala como surgiu a ideia por trás das páginas Index, que comumente, é a página inicial da maioria dos sites.

## UDP e TCP
Dentre os protocolos citados na aula, estão os dois: UDP e TCP. **User Datagram Protocol** e **Transmission Control Protocol**. Esses dois são os principais protocolos de gerenciamento de pacotes da Internet, no entanto, o uso deles depende do objetivo a ser alcançado. Se formos comparar a segurança de dados, em relação a perda de pacotes, o TCP é superior, pois possui uma verificação para garantir que todos os pacotes foram recebidos corretamente (vejam [Acknowledgement](https://en.wikipedia.org/wiki/Acknowledgement_(data_networks))). Enquanto isso, o UDP não garante essa segurança. No entanto, tudo tem seu preço! O TCP, por causa dessa garantia, demanda mais tempo.

O UDP, por sua vez, é mais rápido e por causa disso é geralmente utilizado por serviços como **transmissões ao vivo** e **vídeo-games**. O UDP é usado nesses cenários, pois a perda de pacote é irrisória e pode ser compensada pelos próprios usuários, como quando pedimos para alguém repetir o que disse, pois a chamada havia "travado". No mundo dos jogos, chamamos essa perda de pacotes de **Lag**. Para saber mais sobre isso, veja o vídeo compartilhado pelo próprio Filipe: [HTML5 Games - UDP vs TCP](https://youtu.be/ZEEBsq3eQmg).

## Internet Protocol
**Internet Protocol**, comumente chamado de **IP**, é um protocolo de comunicação usado entre todas as máquinas em rede para encaminhamento dos dados. Usado no modelo **TCP/IP**. Muitas vezes, associamos o termo IP ou **endereço IP**, que por sua vez é um endereço de dispositivo que é rótulado por um conjunto de números.

## Desafio
No fim do dia, o Filipe manda um desafio: colocar o projeto em um link público e enviar esse link para alguém, e então ver qual é a reação dela para a mensagem deixada na página.

Eu resolvi fazer esse desafio mandando o link para o meu melhor amigo, então a mensagem que deixei na página era para ele. Depois, eu precisava encarar a ideia principal do desafio, colocar o projeto no ar!

Para isso, eu usei o Vercel. Eu cheguei nessa conclusão, pois em aulas anteriores, o próprio Deschamps já havia mencionado que era possível hospedar de forma gratuita no Vercel, sendo assim, fiz o **commit** através do `git` para o repositório no GitHub. De lá, o Vercel fez o resto, configurei poucas coisas e pronto, o site estava no ar: [https://hananitallyson-clone-tabnews.vercel.app/](https://hananitallyson-clone-tabnews.vercel.app/).

É interessante mencionar que durante o deploy, o Vercel indicou que o arquivo `.next` não deveria ser enviado dentro do repositório. No dia seguinte, isso vai ser importante...

---

- [Anterior](/dias/dia3.md) - [Próximo](/dias/dia5.md) - [Sumário](../README.md)
