# Segurança de Redes de Computadores

## :page_with_curl: Atividade 7

1. Qual é a diferença entre aleatoriedades estatísticas e imprevisibilidade?

   Aleatoriedade estatística se refere a uma propriedade de uma sequência de números ou letras, de modo que a sequência pareça aleatória e passe por certos testes estatísticos que indicam que a sequência tem as propriedades de aleatoriedade. Se uma sequência estatisticamente aleatória é gerada por um algoritmo, então a sequência é previsível por qualquer um que conheça o algoritmo e o ponto de partida da sequência. Uma sequência imprevisível é aquela em que o conhecimento do método de geração de sequência é insuficiente para determinar a sequência.

2. Liste considerações de projeto importantes para uma cifra de fluxo.

   a) A sequência de criptografia deve ter um período grande.

   b) O fluxo de chaves deverá se aproximar o máximo possível das propriedades de um fluxo de número aleatório verdadeiro.

   c) Para a proteção contra ataques de força bruta, a chave precisa ser suficientemente longa. As mesmas considerações que se aplicam a cifras de bloco são válidas aqui. Assim, com a tecnologia atual, um tamanho de chave de pelo menos 128 bits é desejável.

3. Por que não é desejável reutilizar uma chave de cifra de fluxo?

   Se dois textos claros forem criptografados com a mesma chave usando uma cifra de fluxo, então a criptoanálise geralmente é bem simples. Se os dois fluxos de texto cifrado forem XOR juntos, o resultado será o XOR dos textos claros originais. Se os textos claros forem sequências de texto, números de cartão de crédito ou outros fluxos de bytes com propriedades conhecidas, então a criptoanálise pode ser bem-sucedida.

4. Que operações primitivas são usadas no RC4?

   A criptografia real envolve apenas a operação XOR. A geração de fluxo de chaves envolve a operação de módulo e a troca de bytes.

5. Se apanharmos um algoritmo de congruência linear com um componente aditivo de 0:
   $$X_{n+1} = (aX_n) \mod m$$
   então, podemos mostrar que, se *m* é primo, e se determinado valor de $a$ produz o período máximo de $m − 1$, então $a^k$ também produzirá o período máximo, desde que $k$ seja menor que $m$ e que $m − 1$ não seja divisível por $k$. Demonstre isso usando $X_0 = 1$  e $m = 31$, e produzindo as sequências para $ak = 3, 3^2, 3^3$ e $3^4$.

   Para cada valor de $a^k$, calculamos a sequência:

   $ak = 3$

   $$X_1 = (3X_0) \mod 31 = (3×1) \mod 31 = 3$$

   	E assim por diante. Teremos então os resultados:



	|$1, 3, 9, 27, 19, 26, 16, 17, 20, 29, 25, 13, 8, 24, 10, 30, 28, 22, 4, 12, 5, 15, 14, 11, 2, 6, 18, 23, 7, 21, 1$|
	|--------------------------------------------------------------------------------------------------------------------|                                                                           
	
	E então que $a = 3$. 

6. a) Qual é o período máximo que pode ser obtido do seguinte gerador?

   $$X_{n+1} = (aX_n)  \mod 2^4 $$

   O período máximo é $24–2 = 4$.

   b) Qual deverá ser o valor de $a$?

   $a$ deve ser 3, 5, 11, ou 13.

   c) Que restrições são exigidas na semente?

   A semente deve ser ímpar.

7. Que valor de chave RC4 deixará $S$ inalterado durante a inicialização? Ou seja, após a permutação inicial de $S$, as entradas de $S$ serão quais aos valores de 0 a 255 na ordem crescente.

   Usamos uma chave de tamanho 255 bytes. Os dois primeiros bytes são zero, isto é,  $K[0] = K[1] = 0$. Então temos: $K[2] = 255; K[3] = 254; … K[255]= 2$.

8. O algoritmo Blum Blum Shub é baseado na teoria dos resíduos quadráticos e utiliza três números inteiros para realizar os cálculos: $p, q$ e $s$.

   a) Escolha dois números primos grandes $p$ e $q$, onde $p$ e $q$ sejam congruentes a $3 \mod 4$ e não tenham fatores primos comuns. Por exemplo, você pode escolher $p = 499$ e $q = 503$.

   b) Calcule $n = p ∗ q$. Neste caso, $n$ seria igual a $499 ∗ 503 = 250997$.

   c) Escolha um número inteiro $s$ entre $1$ e $n − 1$ que seja coprimo com $n$. Por exemplo, você pode escolher $s = 17$.

   d) Calcule o valor inicial $x_0 = (s^2)  \mod n$. Neste caso, $x_0$ seria igual a $(17^2) \mod 250997 = 289$.

   e) Agora, vamos gerar uma sequência de números aleatórios usando o algoritmo Blum Blum Shub. Para gerar cada número da sequência, use a seguinte fórmula: $x_i = (x_{i−1}^2) \mod n$.

   f) Execute a fórmula várias vezes para gerar uma sequência de números aleatórios. Por exemplo, você pode executar a fórmula 10 vezes para obter 10 números aleatórios. Aqui está a sequência de números aleatórios gerados usando o algoritmo Blum Blum Shub com os valores do exemplo:

|$289, 253306, 14107, 23546, 67740, 144593, 79829, 46219, 132936, 9863$|  
|----------------------------------------------------------------------|

Qual foi a sua sequência?

a) $p=503$

$q=509$

b) $n=p×q=503×509=255027$

c) $s=19$

d) $x_0​=(s^2) \mod n=(19^2) \mod 255027=361 \mod 255027=361$

f) A sequência gerada foi:

|$361,130321,11996,16842,231075,200667,86410,172699,103344,72058$|
|-|

