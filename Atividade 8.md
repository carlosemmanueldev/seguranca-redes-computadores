# Segurança de Redes de Computadores

## :page_with_curl: Atividade 8

1. Por que $mdc(n, n + 1) = 1$ é para dois inteiros consecutivos $n$ e $n + 1$?
Se $p$ fosse qualquer primo que dividisse $n$ e $n + 1$, ele também teria que dividir $(n + 1) – n = 1$.

2. Usando o teorema de Fermat, encontre $3^{201} \mod 11$.
O Teorema de Fermat afirma que se $p$ é primo e $a$ é um inteiro positivo não divisível por $p$, então $a^{p–1} ≡ 1 (\mod p)$. Portanto $3^{10}
≡ 1 (\mod 11)$. Portanto, $3^{201} = (3^{10})^{20} × 3 ≡ 3 (\mod 11)$.

3. Use o teorema de Fermat para encontrar um número $a$ entre $0$ e $72$, com $a$ congruente a $9794 \mod 73$.
$a =12$.

4. Use o teorema de Euler para encontrar um número $a$ entre $0$ e $9$, tal que $a$ seja congruente a $7^{1000} \mod 10$. (Observe que isso é o mesmo que o último dígito da expansão decimal de $7^{1000}$).
$a = 1$.

5. Use o teorema de Euler para encontrar um número $x$ entre $0$ e $28$, com $x^{85}$ congruente a $6 \mod 35$ (Você não precisará usar qualquer pesquisa por força bruta).
$x = 6$.

6. Observe, na Tabela 8.2, que $φ(n)$ é par para $n > 2$. Isso é verdadeiro para todo $n > 2$. Dê um argumento conciso para explicar por que isso acontece.
Se $a$ é um dos inteiros contados em $φ(n)$, isto é, um dos inteiros
não maior que $n$ e primo de $n$, o $n – 1$ é outro inteiro desse tipo,
porque $mdc(a, n) = mdc(m – a, m)$. Os dois inteiros, $a$ e $n – a$, são
distintos, porque $a = n – a$ dá $n = 2a$, o que é inconsistente com a
suposição de que $mdc(a, n) = 1$. Portanto, para $n > 2$, os inteiros
contados em $φ(n)$ podem ser pareados, e então o número deles deve ser par.

7. Se $n$ é composto e passa no teste de Miller-Rabin para a base $a$, então $n$ é chamado de pseudoprimo forte à base $a$. Mostre que $2047$ é um pseudoprimo à base $2$.
No passo 1 do para testar o $2047$, definimos $k = 1$ e $q = 1023$, porque $(2047 – 1) = (2^1)(1023)$.
Na passo 2, selecionamos $a = 2$ como base.
Na passo 3, temos $a^q \mod n = 2^{1023} \mod 2047 = (2^{11})^{93} \mod 2047 = (2048)^{93} \mod 2047 = 1$. 
E mostramos que $2047$ passa no teste.

8. O exemplo usado por Sun-Tsu para ilustrar o CRT foi
$$x = 2 (mod 3); x = 3 (mod 5); x = 2 (mod 7)$$
Solucione para $x$.
Temos $M = 3 × 5 × 7 = 105; M/3 = 35; M/5 = 21; M/7 = 15$.
O conjunto de congruências lineares:
$35b_1 ≡ 1 (\mod 3); 21b_2 ≡ 1 (\mod 5); 15b_3 ≡ 1 (\mod 7)$
tem as soluções $b_1 = 2; b_2 = 1; b_3 = 1$. Então,
$x ≡ 2 × 2 × 35 + 3 × 1 × 21 + 2 × 1 × 15 ≡ 233 (\mod 105) = 23$
