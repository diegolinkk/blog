---
title: "Recebendo e trabalhando com parâmetros em scripts PHP"
date: 2022-10-17T21:30:27-03:00
draft: false
tags: ["php", "colinha"]
---

Nesse rápido post, vamos entender como receber argumentos vindos da linha de comando ao chamar um script PHP.

## A variável $ARGV
O elemento chave dessa questão é a variável pré definida $ARGV. 

Essa variável do tipo array e esta  armazena todos os parâmetros passados para o script.
O primeiro elemento do array é sempre o nome do script e os demais são os argumentos passados.

## Exemplo

Vamos criar um script que exibe:
- o nome do script
- o primeiro argumento passado
- o segundo passado

{{<highlight php>}}

$nomeDoScript = $argv[0]; //o primeiro argumento é sempre o nome do arquivo
$parametro1 = $argv[1];
$parametro2 = $argv[2];

echo "O nome do script é {$nomeDoScript}" . PHP_EOL;
echo "Os parâmetros recebidos foram {$parametro1} e {$parametro2}";
{{</highlight>}}

Agora vamos chamar o nosso script, que atualmente se chama script.php:

{{<highlight bash>}}
> php .\script.php 100 200
{{</highlight>}}

A saída no terminal será:

{{<highlight terminal>}}
O nome do script é .\script.php
Os parâmetros recebidos foram 100 e 200
{{</highlight>}}

Vale lembrar que caso eu passe mais do que dois parâmetros, o script não apresentará nenhum erro, porém, caso eu passar menos argumentos do que o script utiliza (que nesse caso são dois), o PHP sobe um erro de "Undefined array key...".

Por hoje é só

Fonte: https://www.php.net/manual/pt_BR/reserved.variables.argv.php