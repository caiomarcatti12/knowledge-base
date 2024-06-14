# A Importância de Fixar a Versão da Instalação dos Pacotes em um Container Docker

Fala galera, tudo bem? Bora falar sobre um assunto importante pra quem mexe com Docker: a importância de fixar a versão dos pacotes. Isso aí pode parecer chato e desnecessário mas é essencial pra evitar dor de cabeça no futuro.

Vou te passar um caso que vivenciei recentemente que quebrou todo meu pipeline e me deu uma dor de cabeça, desnecessária.

## O Problema da Variabilidade
Então, o lance é o seguinte: se você não fixa as versões dos pacotes, cada vez que você reconstrói um container, pode acabar pegando versões diferentes dos pacotes. E aí, meu amigo, começam os problemas. Atualizações pode trazer mudanças que quebra seu código ou introduzir novos bugs.

## Exemplos de Problemas Comuns
- Compatibilidade de Dependências: Às vezes, um pacote depende de uma versão específica de outro pacote. Se um deles atualizar e o outro não, já era.
- Mudanças de API: Novas versões pode mudar como você deve usar o pacote, o que pode quebrar sua aplicação.
- Bugs Introduzidos: Atualizações pode trazer novos bugs. 


Sim, isso acontece! Olha aqui... No momento do build da imagem quebrou.
![breaking-changes.png](./breaking-changes.png)

## Benefícios de Fixar Versões
- Consistência: Fixar as versões dos pacotes garante que o ambiente de desenvolvimento, testes e produção seja o mesmo. Isso é bom porque você sabe que se funcionou em um lugar, vai funcionar nos outros também.
- Reprodutibilidade: A cada build vai gerar o mesmo resultado. Isso é crucial pra um deploy tranquilo e sem surpresas.
- Segurança: Você também pode aplicar patches de segurança de maneira controlada. Se você sabe exatamente quais versões tá usando, fica mais fácil identificar e corrigir vulnerabilidades.

## Meu caso
A alguns meses atrás eu contrui uma imagem baseada na alpine 3.19 com o php8.2 na versão 8.2.19-r0 e na imagem abaixo percebe que a data de build do pacote php82 na versão 8.2.20-r0 foi realizada no dia 06/06/2024.

![alpine-3-19-php8-2-20-r0.png](./alpine-3-19-php8-2-20-r0.png)

Essa nova versão de build corrigiu 3 vulnerabilidades de segurança. Sendo: 

- [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-4577](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-4577)
- [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-5458](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-5458)
- [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-5585](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-5585)

Vocês podem conferir diretamente no commit do registry do alpine 
[https://git.alpinelinux.org/aports/commit/?id=a7abe5f43dd2884bec684cf11f794dc8854fdba4](https://git.alpinelinux.org/aports/commit/?id=a7abe5f43dd2884bec684cf11f794dc8854fdba4), pow bacana, menos 3 problemas pra nos preocupar e o que isso tem de errado? Nada.

Mas ocorreu dos builds da imagem que estavam utilizando a versão "8.2.19-r0" quebrarem, simplesmente porque "removeram" a versão que eu estava utilizando.

O que me deixou de cabelo em pé é segurança... que de certa forma fiquei extremamente feliz porque parou de funcionar o deploy. Sim, pq parou de funcionar e não estou louco.

Simplesmente porque tive a oportunidade entender o que ocorreu e me levou a conclusão dos seguintes pontos

## Conclusão
- Fixando as versões tenho um controle maior sobre a minha imagem docker.
- Não tenho surpresas de um "componente" ou "biblioteca" mudar o comportamento.
- #ArrumeiParaCabeca... Precisarei atualizar a versão das bibliotecas e garantir a compatibilidade com o software kkkk
- Estou seguindo as boa práticas 
- Depois de atualizar o software continuou funcionando como o esperado <3

## Indagação

Ainda sim, mesmo fixando a versão e sabendo que meu software vai se comportar da mesma maneira em diversos ambientes, que não terei tantas emoções e surpresas com algo que não tenho o controle diretamente, me levou a fritar nos seguinte pontos.

- Quem disse que só por eu seguir uma boa prática o software está seguro?
- Nesse caso fizeram o bem, corrigiram algumas CVE's e fizeram um patch de correção.
- Se no caso de uma correção de vulnerabilidade, realmente fosse a introdução de um bug?
- Se fosse a introdução de uma vulnerabilidade? Nunca pensei por esse lado, pois sempre atualizo os softwares para as últimas versões e não "vejo" realmente o que tá sendo alterado.

Poxa, agora colocando na balança, o fato dele ter "deletado" a tag foi bom, pois pude ver a mudança que ocorreu

E se ele simplesmente "deletasse" a tag e coloca-se outra no lugar? 0.0

Isso me leva a acreditar que eu não estou programando sozinho que o container não é só meu, estou trabalhando com um desconhecido, como posso confiar nele? Será que posso confiar?

Poxa, ficarei sem respostas e fritando pra achar uma resposta... não somente de como me proteger de bugs e vulnerabilidades, mas também de um "desconhecido" manipular o meu "software".
