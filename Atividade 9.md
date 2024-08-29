# Segurança de Redes de Computadores

## :page_with_curl: Atividade 9

1. Quais são os principais elementos de um criptossistema de chave pública?
Texto claro, algoritmo de criptografia, chaves públicas e privadas, texto cifrado e algoritmo de descriptografia.

2. Quais são os papéis da chave pública e da privada? Descreva-os com detalhes e com exemplos.
A chave privada de um usuário é mantida privada e conhecida apenas pelo usuário. A chave pública do usuário é disponibilizada para outros usarem. A chave privada pode ser usada para criptografar uma assinatura que pode ser verificada por qualquer pessoa com a chave pública. Ou a chave pública pode ser usada para criptografar informações que só podem ser descriptografadas pelo possuidor da chave privada.

3. Quais requisitos os criptossistemas de chave pública precisam cumprir para serem considerados como um algoritmo seguro?
É computacionalmente fácil para um usuário B gerar um par (chave pública $PU_b$, chave privada $PR_b$).
É computacionalmente fácil para um remetente A, conhecendo a chave pública e a mensagem a ser criptografada, $M$, gerar o texto cifrado
correspondente: $C = E(PU_b, M)$
É computacionalmente fácil para o receptor B decifrar o texto cifrado resultante usando a chave privada para recuperar a mensagem original: $M = D(PR_b, C) = D(PR_b, E(PU_b, M))$
É computacionalmente inviável para um usuário invasor, conhecendo a chave pública, $PU_b$, determinar a chave privada, $PR_b$.
É computacionalmente inviável para um usuário invasor, conhecendo a chave pública, $PU_b$, e um texto cifrado, $C$, recuperar a mensagem original, $M$.

4. Descreva, em termos gerais, um procedimento eficiente para se escolher um número primo.
	1) Escolha um inteiro ímpar $n$ aleatoriamente (por exemplo, usando um gerador de números pseudoaleatórios).
	2) Escolha um inteiro $a < n$ aleatoriamente.
	3) Execute o teste de primalidade probabilística, como Miller-Rabin. Se $n$ falhar no teste, descarte o valor de $n$ e volte para a etapa 1.
	4) Se $n$ passou por um número suficiente de testes, aceite $n$; caso contrário, volte para a etapa 2.

5. Antes da descoberta de quaisquer esquemas de chave pública específicas, como RSA, uma prova de existência foi desenvolvida, cuja finalidade era demonstrar que a encriptação de chave pública é possível em teoria. Considere as funções $f_1(x_1) = z_1$; $f_2(x_2, y_2) = z_2$; $f_3(x_3, y_3) = z_3$, onde todos os valores são inteiros com $1 ≤ x_i, y_i, z_i ≤ N$. A função $f_1$, pode ser representada por um
vetor $M_1$ de tamanho $N$, em que a k-ésima entrada é o valor de $f_1(k)$. De modo semelhante, $f_2$ e $f_3$ podem ser representados pelas matrizes $M2$ e $M3$ de tamanho $N × N$. A intenção é indicar o processo de encriptação/decriptação por pesquisas de tabela para aquelas com valores muito grandes de $N$. Essas tabelas seriam impraticavelmente grandes, mas, a princípio, poderiam ser construídas. O esquema funciona da seguinte forma: construa $M1$ com uma permutação aleatória de todos os inteiros entre $1$ e $N$; ou seja, cada inteiro aparece exatamente uma vez em $M1$. Construa $M2$, de modo que cada linha contenha uma permutação aleatória dos primeiros $N$ inteiros. Finalmente, preencha $M3$ para satisfazer a seguinte condição:
$$f_3(f_2(f_1(k), p), k) = p$$ para todo $k, p$ com $1 ≤ k, p ≤ N$

	Resumindo,
	1) $M1$ toma uma entrada $k$ e produz uma saída $x$.
	2) $M2$ toma as entradas $x$ e $p$, dando a saída $z$.
	3) $M3$ toma as entradas $z$ e $k$ e produz $p$.

	As três tabelas, uma vez construídas, se tornam públicas.
	a) Deverá ficar claro que é possível construir $M3$ para satisfazer a condição anterior. Como um exemplo, preencha $M3$ para o caso simples a seguir:

	$$
	\text{M1} = 
	\begin{bmatrix}
	5 \\
	4 \\
	3 \\
	2 \\
	1
	\end{bmatrix}
	\quad
	\text{M2} = 
	\begin{bmatrix}
	5 & 2 & 3 & 4 & 1 \\
	4 & 2 & 5 & 1 & 3 \\
	1 & 3 & 2 & 4 & 5 \\
	3 & 1 & 4 & 2 & 5 \\
	2 & 5 & 3 & 4 & 1
	\end{bmatrix}
	\quad
	\text{M3} = 
	\begin{bmatrix}
	a_1 & a_2 & a_3 & a_4 & a_5 \\
	b_1 & b_2 & b_3 & b_4 & b_5 \\
	c_1 & c_2 & c_3 & c_4 & c_5 \\
	d_1 & d_2 & d_3 & d_4 & d_5 \\
	e_1 & e_2 & e_3 & e_4 & e_5
	\end{bmatrix}
	$$

	Convenção: o i-ésimo elemento de $M1$ corresponde a $k = i$. A i-ésima linha de $M2$ diz respeito $ax = i$; a j-ésima coluna de $M2$ equivale a $p = j$. A i-ésima linha de $M3$ indica $z = i$; a j-ésima coluna de $MB$ relaciona-se a $k = j$. 	
	a) Descreva o uso desse conjunto de tabelas para realizar a encriptação e decriptação entre dois usuários. 
	Preenchendo $M3$:
	$\quad
	\text{M3} = 
	\begin{bmatrix}
	5 & 2 & 1 & 4 & 5 \\
	1 & 4 & 3 & 2 & 2 \\
	3 & 1 & 2 & 5 & 3 \\
	4 & 3 & 4 & 1 & 4 \\
	2 & 5 & 5 & 3 & 1 
	\end{bmatrix}$
	Suponha que uma mensagem de texto simples $p$ deva ser criptografada por um usuário A e enviada para um usuário B. B faz uso de $M1$ e $M3$, e A faz uso de $M2$. B escolhe um número aleatório, $k$, como sua chave privada, e mapeia $k$ por $M1$ para obter $x$, que ele envia como sua chave pública para A. A usa $x$ para criptografar $p$ com $M2$ para obter $z$, o texto cifrado, que ela envia para B.
B usa $k$ para descriptografar $z$ por meio de $M3$, produzindo a mensagem de texto claro $p$.

	b) Demonstre que esse é um esquema seguro
	Se os números forem grandes o suficiente, e $M1$ e $M2$ forem suficientemente aleatórios para tornar impraticável trabalhar de trás para frente, $p$ não pode ser encontrado sem conhecer $k$.

6. Realize a encriptação e decriptação usando o algoritmo RSA, como na Figura 9.5, para o seguinte:
	a) $p = 3; q = 11, e = 7; M = 5;$
	$n = 33; φ(n) = 20; d = 3; C = 26.$
	
	b) $p = 5; q = 11, e = 3; M = 9;$
	$n = 55; φ(n) = 40; d = 27; C = 14.$
	
	c) $p = 7; q = 11, e = 17; M = 8;$
	$n = 77; φ(n) = 60; d = 53; C = 57.$
	
	d) $p = 11; q = 13, e = 11; M = 7;$
	$n = 143; φ(n) = 120; d = 11; C = 106.$
	
	e) $p = 17; q = 31, e = 7; M = 2.$
	$n = 527; φ(n) = 480; d = 343; C = 128.$ Para decriptação, temos que $128^{343} \mod 527= 128^{256} × 128^{64} × 128^{16} × 128^{4} × 128^{2} × 128^{1} \mod 527 = 35 × 256 × 35 × 101 × 47 × 128 = 2 \mod 527 = 2 \mod 257$

	Dica: a decriptação não é tão difícil quanto você pensa; use alguma sutileza.

7. Em um sistema de chave pública usando RSA, você intercepta o texto cifrado $C = 10$ enviado a um usuário cuja chave pública é $e = 5, n = 35$. Qual é o texto claro $M$?
$5$.

