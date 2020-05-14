---
title: "Compartilhando pasta local com Container no Docker Toolbox"
date: 2020-05-14T16:15:00+01:00
draft: false
tags: ["docker"]
---

Para compartilhar arquivos entre host e container, devemos montar um volume e fazer a ligação entre eles pelo comando:

{{<highlight docker >}}
docker container run -v "/c/Users/diego/Html/":/home/diego -it ubuntu bash
{{</highlight >}}

### Explicando comando:
{{<highlight docker >}} docker container run # comando básico do docker para executar/iniciar um container {{</highlight >}}

{{<highlight docker >}} -v "/c/Users/diego/Html/":/home/diego #aqui de fato estamos criando o volume, colocando o caminho da pasta na qual quero compartilhar na primeira metade e o ponto a ser montado no container na segunda metade {{</highlight >}}

{{<highlight docker >}}-it ubuntu bash # -it são parâmetros que nos permitem controlar o container e bash é o aplicativo a ser excutado, no caso vamos executar um bash dentro do container {{</highlight>}}

Sendo o primeiro caminho relativo ao diretório do host, e o segundo sendo o ponto de montagem. 

## Observação importante
Por alguma limitação, o docker toolbox NÃO permite compartilhamento de arquivos que estejam fora da pasta do usuário

### fonte
1. [docker-sharing-a-volume-on-windows-with-docker-toolbox](https://stackoverflow.com/questions/34161352/docker-sharing-a-volume-on-windows-with-docker-toolbox)