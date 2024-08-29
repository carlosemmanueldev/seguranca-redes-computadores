﻿# Segurança de Redes de Computadores

## :page_with_curl: Atividade 4

1. Defina resumidamente, um grupo, um anel, um corpo.

   Um grupo é um conjunto de elementos que é fechado sob uma operação binária e que é associativo e que inclui um elemento identidade e um elemento inverso.

   Um anel é um conjunto de elementos que é fechado sob duas operações binárias, adição e subtração, com o seguinte: a operação de adição é um grupo que é comutativo; a operação de multiplicação é associativa e é distributiva sobre a operação de adição.

   Um corpo é um anel no qual a operação de multiplicação é comutativa, não tem divisores de zero e inclui um elemento identidade e um elemento inverso.

2. O que significa dizer que *b* é um divisor de *a*?

   Um *b* diferente de zero é um divisor de *a* se *a = mb* para algum *m*, onde *a*, *b* e *m* são inteiros. Ou seja, *b* é um divisor de *a* se não houver resto na divisão.

3. Para cada uma das seguintes equações, encontre um inteiro *x* que satisfaça:

   a) 5x ≡ 4 (mod 3)

   2

   b) 7x ≡ 6 (mod 5)

   3

   c) 9x ≡ 8 (mod 7)

   4

4. Encontre o inverso multiplicativo de cada elemento diferente de zero em *Z₅*.

   Elemento 1:

   1 × x ≡ 1 (mod 5)

   O inverso multiplicativo de 1 é 1, pois 1 × 1 ≡ 1 (mod 5)


	 Elemento 2:
	
	 2 × x ≡ 1 (mod 5)
	
	 Testando valores:
	
	 Se x = 1 então 2 × 1 = 2 (não é um módulo 5)
	
	 Se x = 2 então 2 × 2 = 4 (não é um módulo 5)
	
	 Se x = 3 então 2 × 3 = 6 ≡ 1 (mod 5)
	
	 Assim, o inverso multiplicativo de 2 é 3.
	
	
	 Elemento 3:
	
	 3 × x ≡ 1 (mod 5)
	
	 Testando valores:
	
	 Se x = 1 então 3 × 1 = 3 (não é um módulo 5)
	
	 Se x = 2 então 2 × 3 = 6 ≡ 1 (mod 5)
	
	 Assim, o inverso multiplicativo de 3 é 2.
		
	 Elemento 4:
	
	 4 × x ≡ 1 (mod 5)
		
	 Testando valores:
	
	 Se x = 1 então 4 × 1 = 4 (não é um módulo 5)
	
	 Se x = 2 então 4 × 2 = 8 ≡ 3 (mod 5) (não é um módulo 5)
	
	 Se x = 3 então 4 × 3 = 12 ≡ 2 (mod 5) (não é um módulo 5)
	
	 Se x = 4 então 4 × 4 = 16 ≡ 1 (mod 5)
	
	 Portanto, o inverso multiplicativo de 4 é 4.

5. Determine os MDC:

   a) mdc(24140, 16762):

   $$mdc(24140, 16762) = mdc(16762, 7378) = mdc(7378, 2006) = mdc(2006, 1360) = mdc(1360, 646) = mdc (646, 68) = mdc(68, 34) = mdc(34, 0) = 34$$

   b) mdc(4655, 12075).

   35

6. Usando o algoritmo de Euclides estendido, encontre o inverso multiplicativo de:

   a) 1234 mod 4321;

   3239


	 b) 24140 mod 40902;
			
	  mdc(40902, 24240) = 34 ≠1, então não há inverso multiplicativo.
			
		
	 c) 550 mod 1769.
			
	  550

7. Determine o inverso multiplicativo de *x³ + x + 1* em GF(2⁴), com *m(x) = x⁴ + x + 1.*

   *x² + 1*

8. Para a aritmética de polinômios com coeficientes em *Z₁₀*, realize os seguintes cálculos:

   (a) (7x + 2) − (x² + 5)

   = 7x + 2 − x² − 5

   = −x² + 7x + (2 − 5)

   = −x² + 7x + 3

   **= 9x² + 7x + 7**


	 (b) (6x² + x + 3) × (5x² + 2)
		
	 = 30x⁴ + 12x² + 5x³ + 2x + 15x² + 6
		
	 30x⁴ ≡ 0x⁴(mod10) (porque 30 ≡ 0)
		
	 12x² + 15x² = 27x² ≡ 7x² (mod10)
		
	 **= 5x³ + 7x² + 2x + 6**

9. Estruture uma calculadora simples de quatro funções em GF(2⁴). Você pode usar uma tabela com valores pré-calculados para os inversos multiplicativos.
