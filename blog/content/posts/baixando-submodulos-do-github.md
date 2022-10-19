---
title: "Baixando submódulo do Github"
date: 2022-10-18T22:30:27-03:00
draft: false
tags: ["git", "github", "colinha"]
---

Nesse post vamos entender como baixar submódulos do Github juntamente com o clone do projeto.

## O que são submódulos do git ?

Em resumo, é um git dentro de outro git.

## Mas pra que isso serve ?

Digamos que você esteja desenvolvendo um blog que utiliza um template de terceiro. Esse template por sua vez, tem seu próprio repositório git e seria interessante que você mantivesse sempre essa pasta atualizada no seu atual repositório, seja lá por motivos de segurança ou de otimização.
Para que você não precise ficar baixando esse módulo separado da sua pasta e copiar/colar em seguida no seu repositório, você pode adicionar um "git de terceiro" dentro do  seu repositório e atualizar sempre que você quiser (normalmente com git pull). Esse recurso é chamado de submódulo no git.

## Adicionando um submódulo no meu repositório.

Dentro do seu repositório git já iniciado, você deve escolher uma subpasta e apontar o link do repositório através do comando abaixo, digamos que você vai adicionar o submódulo na pasta de nome "teste":

{{<highlight bash>}}
# o link é de um repositório válido do github
# da mesma forma que fazemos com o git clone
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git teste
{{</highlight>}}

Pronto, agora toda vez que eu quiser atualizar essa pasta com o seu repositório git, eu entro dentro dessa pasta e executo o "git pull" da mesma forma que faríamos com qualquer outro projeto.

## E quando eu baixar meu repositório, ja vem tudo junto ?

A resposta é não, a pasta vem baixada, porém vem vazia, mas isso é fácil de resolver, basta adicionar o comando --recursive:

{{<highlight bash>}}
git push [https://link-do-seu-projeto.git] --recursive
{{</highlight>}}

pronto, tudo nos conformes

## E para listar os submódulos que meu projeto tem:

Simples:
{{<highlight bash>}}
git submodule
{{</highlight>}}

A saída vai ser algo parecido com isso:
{{<highlight bash>}}
1b21063360f0f7905f0ae9d736d14da0c4393e87 blog/public (heads/master)
+0340796dd5889154b8d1e71d09b75bf2883f2bab blog/themes/ananke (v2.5.6-113-g0340796)
{{</highlight>}}

Nessa saída, temos dois submódulos, sendo que o primeiro está na pasta blog/public e o segundo está em blog/themes/ananke.

## Como eu vejo o link do repositório do submódulo ?
Com a informação acima em mãos, eu posso ir na pasta do repositório, por exemplo, na pasta blog/public:
{{<highlight bash>}}
cd blog/public
{{</highlight>}}

E executar o comando git remote --verbose para verificar o link do repositório remoto:
{{<highlight bash>}}
git remote -v
{{</highlight>}}

A saída vai ser mais ou menos assim:
{{<highlight bash>}}
origin  https://github.com/theNewDynamic/gohugo-theme-ananke.git (fetch)
origin  https://github.com/theNewDynamic/gohugo-theme-ananke.git (push)
{{</highlight>}}

Se você quiser um repositório de exemplo que contenha submódulos reais, você pode clonar o repositório git desse blog no link abaixo:

https://github.com/diegolinkk/blog

Por hoje é só.

## Fontes
- https://pt.stackoverflow.com/questions/111313/para-que-serve-um-submodule-no-git
- https://github.com/theNewDynamic/gohugo-theme-ananke