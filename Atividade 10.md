# Segurança de Redes de Computadores

## :page_with_curl: Atividade 10

1. Os usuários A e B utilizam a técnica de troca de chaves Diffie-Hellman com um primo comum $q = 71$ e uma raiz primitiva $α = 7$.

   a) Se o usuário A tem chave privada $X_A = 5$, qual é a chave pública de A, $Y_A$?

   $Y_A = 7^5 \mod 71= 51$.

   b) Se o usuário B tem chave privada $X_B = 12$, qual é a chave pública de B, $Y_B$?

   $Y_B = 7^{12} \mod 71= 4$.

   c) Qual é a chave secreta compartilhada?

   $K = 45 \mod 71= 30$.

2. Considere um esquema Elgamal com um primo comum $q = 71$ e uma raiz primitiva $α = 7$.

   a) Se B tem chave pública $Y_B = 3$ e A escolheu um inteiro aleatório $k = 2$, qual é o texto cifrado de $M = 30$?

   (49, 57).

   b) Se A, então, selecionar um valor diferente de $k$, de modo que a codificação de $M = 30$ seja $C = (59, C_2)$, qual é o inteiro $C_2$?

   $C_2 = 29$.

3. Demonstre que as duas curvas elípticas da Figura 10.4 satisfazem, cada uma, às condições para um grupo sobre os números reais.

   Usamos a equação (10.1), que define a forma da curva elíptica como

   $y^2 = x^3 + ax + b$, e a equação (10.2), que diz que uma curva elíptica sobre os números reais define um grupo se $4a^3 + 27b^2 ≠ 0$.

   a) Para $y^2 = x^3 – x$, temos $4(–1)^3 + 27(0) = –4 ≠ 0$.

   b) Para $y^2 = x^3 + x + 1$, temos $4(1)^3 + 27(1) = 31 ≠ 0$.

4. $(4, 7)$ é um ponto na curva elíptica $y^2 = x^3 − 5x + 5$ sobre números reais?

   Sim. Já que a equação é verdadeira para $x = 4$ e $y = 7$:

   $7^2= 4^3 – 5(4) + 5$

   $49 = 64 – 20 + 5 = 49$
