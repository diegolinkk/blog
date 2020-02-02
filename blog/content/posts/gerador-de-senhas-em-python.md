---
title: "Gerador De Senhas Em Python"
date: 2020-02-01T16:08:27-03:00
draft: false
---

Nesse post nós vamos criar um gerador de senhas simples em Python. 
Este gerador foi construido para fins didáticos e pode ser utilizado caso você precise gerar senhas que não possuam nenhum viés humano.

## Conhecimento aplicado no tutorial
Esse algorítmo foi feito em python e utiliza alguns recursos básicos da linguagem:

1. Importação de bibliotecas
2. Funções
3. Listas
4. Laços de repetição

## Escopo do gerador de senhas

Para dar uma certa liberade ao usuário, o nosso gerador permitirá que o mesmo escolha algumas variáveis:

1. Quantidade de senhas geradas
2. Tamanho (em caracteres) das senhas
3. Tipo de senha (letras, numeros e caracteres especiais)

## Por que seu script não aceita argumentos na chamada do script ?

Nesse ponto algumas pessoas podem sugerir que esses argumentos sejam passados durante a execução do script ao invés de precisar abrir o código fonte e fazer as chamadas de função manualmente mas eu preferi deixar essa funcionalidade de lado para diminuir a complexidade do script e facilitar a compreensão do algorítmo.

## Código

{{< highlight python >}}

#bibliotéca que escolhe um elemento aleatório de determinada lista
from random import choice 

#definindo a lista dos caracteres que definem a complexidade das senhas. 

letras = ['a','b','c','d','e','f','g','h','i','j',
'k','l','m','n','o','p','q','r','s','t','u','v','w','x',
'y','z']

numeros = ['1','2','3','4','5','6','7','8','9','0']

caracteres_especiais = ['@',',','#','$','&','*','(',')','+','-']

#criando a função que aceita três argumentos
def gerador_de_senhas(quantidade = 1,tamanho = 8, tipo = 1):
    #definindo os caracteres que vão compor a senha
    if tipo == 1:
        caracteres = letras
    elif tipo == 2:
        caracteres = letras + numeros
    else:
        caracteres = letras + numeros + caracteres_especiais

    senhas = [] #lista de senhas

    #nos laços for, utilizamos _ (underline) quando 
    #não utilizamos o passo dentro do laço
    for _ in range(quantidade):
        senha = "" #limpa a senha novamente

        #laço se repete pra cada vez definida no tamanho
        for _ in range(tamanho):
            senha += choice(caracteres)

        #inclui senha formada na lista de senhas
        senhas.append(senha) 
    return senhas

#agora utilizando a função variando tipo, tamanho e quantidade
senhas_tipo_1 = gerador_de_senhas(5,10,1)
senhas_tipo_2 = gerador_de_senhas(10,15,2)
senhas_tipo_3 = gerador_de_senhas(25,6,3)

#mostrando as senhas
print(senhas_tipo_1)
print(senhas_tipo_2)
print(senhas_tipo_3)

{{< /highlight >}}

## Conclusão
Espero que tenham gostado do post e em caso de dúvidas, podem me procurar no [twitter](https://twitter.com/diegolinkk)


### fontes

1. Variáveis não utilizadas em laços de repetição [link](https://stackoverflow.com/questions/5477134/how-can-i-get-around-declaring-an-unused-variable-in-a-for-loop)
2. Utilizando a função random.choice [link](https://pynative.com/python-random-choice/)