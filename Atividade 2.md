# Segurança de Redes de Computadores

## :page_with_curl: Atividade 2

1. Responda (de forma objetiva) as questões a seguir:

	a) Quais são os elementos essenciais de uma cifra simétrica?

   Algoritmo de encriptação, texto claro, chave secreta, texto cifrado e algoritmo de decriptação.

   b) Quais são as duas funções básicas usadas nos algoritmos de encriptação?

   Substituição e permutação.

   c) Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?

   Uma cifra de fluxo é aquela que criptografa um fluxo de dados digitais em um bit ou um 		byte de cada vez. Uma cifra de bloco é aquela em que um bloco de texto claro é tratado como um todo e usado para produzir um bloco de texto cifrado de igual comprimento.

   d) Quais são as duas técnicas gerais para atacar uma cifra?

   Criptoanálise e ataque por força bruta.

   e) Quais são os dois problemas com o one-time pad?

   Primeiro temos o problema de fazer grandes quantidades de chaves aleatórias. Qualquer sistema muito utilizado pode exigir milhões de caracteres aleatórios regularmente. Fornecer caracteres realmente aleatórios com esse volume é uma tarefa significativa.
   O outro problema é o da distribuição e proteção de chaves. Para que cada mensagem seja enviada, uma chave de mesmo comprimento é necessária tanto para o remetente quanto para o destinatário. Portanto, existe um problema gigantesco de distribuição de chaves.

   f) O que é uma cifra de transposição?

   Uma cifra de transposição envolve uma permutação das letras do texto claro.

   g) O que é esteganografia?

   A esteganografia envolve ocultar a existência de uma mensagem.

2. Uma generalização da cifra de César, conhecida como cifra de César afim, tem a seguinte forma:
   a cada letra de texto claro p, substitua-a pela letra de texto cifrado C :
   *C = E([a, b], p) = (ap + b) mod 26*
   um requisito básico de qualquer algoritmo de encriptação é que ele seja um para um. Ou seja, se *p* ≠ *q*, então *E(k, p)* ≠ *E(k, q)*. Caso contrário, a decriptação é impossível, pois mais de um caractere de texto claro é mapeado no mesmo caractere de texto cifrado. A cifra de César afim não é um-para-um para todos os valores de a. Por exemplo, para *a = 2* e *b = 3*, então *E([a, b], 0) = E([a, b], 13) = 3*.

   a) existem limitações sobre o valor de *b*? Explique por que sim ou por que não.

   Não. Uma mudança no valor de b muda a relação entre letras do texto claro e letras do 	texto cifrado para a esquerda ou direita uniformemente, de modo que se o mapeamento for um para um, ele permanece um para um.

   b) determine quais valores de *a* não são permitidos.

   2, 4, 6, 8, 10, 12, 13, 14, 16, 18, 20, 22, 24. Qualquer valor de *a* maior que 25 é equivalente à *a* mod 26.

   c) ofereça uma afirmação geral sobre quais valores de *a* são e não são permitidos. Justifique-a.

   Os valores de *a* e 26 não devem ter nenhum fator inteiro positivo comum além de 1. Isso é equivalente a dizer que *a* e 26 são coprimos, ou que o máximo divisor comum de *a* e 26 é 1. Para ver isso, primeiro observe que *E(a, p) = E(a, q) (0 ≤p≤q< 26)* se e somente se *a(p– q)* for divisível por 26.

	1. Suponha que *a* e 26 sejam coprimos. Então, *a(p– q)* não é divisível por 26, porque não há como reduzir a fração *a/26* e *(p– q)* é menor que 26.
   
	2. Suponha que *a* e 26 tenham um fator comum *k> 1*. Então *E(a, p) = E(a, q)*, se *q = p + m / k*≠*p*

3. a) Encripte a mensagem “meet me at the usual place at ten rather than eight oclock” usando a cifra de Hill com a chave

```math
\begin{pmatrix}
9 & 4 \\
5 & 7
\end{pmatrix}
```

Mostre seus cálculos e o resultado.

Precisamos de um número par de letras, então anexamos um *"q"* ao final da mensagem. Então convertemos as letras nas posições alfabéticas correspondentes:

| m | e | e | t | m | e | a | t | t | h | e | u | s | u | a | l | p | l | a | c | e | a | t | t | e | n | r | a | t | h | e | r | t | h | a | n | e | i | g | h | t | o | c | l | o | c | k | q |  
| --- |---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 13 | 5 | 5 | 20 | 13 | 5 | 1 | 20 | 20 | 8 | 5 | 21 | 19 | 21 | 1 | 12 | 16 | 12 | 1 | 3 | 5 | 1 | 20 | 20 | 5 | 14 | 18 | 1 | 20 | 8 | 5 | 18 | 20 | 8 | 1 | 14 | 5 | 9 | 7 | 8 | 20 | 15 | 3 | 12 | 15 | 3 | 11 | 17 |

Os cálculos são feitos duas letras de cada vez. O primeiro par:

```math
\begin{pmatrix}
C_1 \\
C_2
\end{pmatrix}
=
\begin{pmatrix}
9 & 4 \\
5 & 7
\end{pmatrix}
\begin{pmatrix}
13 \\
5
\end{pmatrix}
\mod 26
=
\begin{pmatrix}
137 \\
100
\end{pmatrix}
\mod 26
=
\begin{pmatrix}
7 \\
22
\end{pmatrix}
```




Os dois primeiros caracteres do texto cifrado são as posições alfabéticas 7 e 22, que correspondem a GV. O texto cifrado completo:

	    GVUIGVKODZYPUHEKJHUZWFZFWSJSDZMUDZMYCJQMFWWUQRKR

b) Mostre os cálculos para a decriptação correspondente do texto cifrado a fim de recuperar o texto claro original.

Primeiro, realizamos uma inversão de matriz. Note que o determinante da matriz de criptografia é (9 ×7) – (4 ×5) = 43. Usando a fórmula de inversão de matriz do livro:

```math
\begin{pmatrix}
9 & 4 \\
5 & 7
\end{pmatrix}^{-1}
=
\frac{1}{43}
\begin{pmatrix}
7 & -4 \\
-5 & 9
\end{pmatrix}
\mod 26
=
23
\begin{pmatrix}
7 & -4 \\
-5 & 9
\end{pmatrix}
\mod 26
=
\begin{pmatrix}
161 & -92 \\
-115 & 9
\end{pmatrix}
\mod 26
=
\begin{pmatrix}
5 & 12 \\
15 & 25
\end{pmatrix}
```


Aqui usamos o fato de que (43) = 23 em *Z*. Uma vez que a matriz inversa 26 foi determinada, a descriptografia pode prosseguir.

4. Elabore um programa que possa encriptar e decriptar usando a cifra de César geral, também conhecida como cifra aditiva.

5. Elabore um programa que possa realizar um ataque de frequência de letra em uma cifra aditiva sem intervenção humana. Seu software deverá produzir textos claros possíveis em ordem aproximada de probabilidade. Seria bom se a sua interface com o usuário permitisse que ele especificasse “mostre os 10 textos claros mais prováveis”.

6. Crie um software que possa encriptar e decriptar usando uma cifra de Hill 2 × 2.

