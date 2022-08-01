---
title: "Como Listar e conectar à Databases, listar tabelas e fazer queries no Postgres"
date: 2022-07-31T12:30:27-03:00
draft: false
tags: ["postgres", "colinha"]
---

## Motivação e formato do post

Esse post segue um modelo de colinha onde constantemente me vejo fazendo repetidas pesquisas no google para executar alguns comandos que são triviais mas a depender do período em que eu não uso determinada ferramenta (como é o caso do Postgres), eu acabo esquecendo. Então vamos lá:

_Obs: todos os comandos já partem da premissa que você esteja conectado ao postgres_

1. Listar database
{{<highlight postgres>}}\l {{</highlight>}}
2. Conectar à database
{{<highlight postgres>}}\c nome_da_database {{</highlight>}}
1. Listar tabelas (já conectado à database)
{{<highlight postgres>}}\dt {{</highlight>}}
1. Query simples sobre uma tabela
{{<highlight postgres>}}\select * from nome_da_tabela; {{</highlight>}}

fontes:
1. [Blog da Jéssica Temporal](https://jtemporal.com/venv-inicio/) de onde tirei a idéia de colinhas. 