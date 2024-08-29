﻿# Segurança de Redes de Computadores

## :page_with_curl: Atividade 5

1. Qual foi o conjunto original de critérios usados pelo NIST para avaliar as cifras AES candidatas?

   **Segurança:** Segurança real; aleatoriedade; solidez, outros fatores de segurança.
   **Custo:** Requisitos de licenciamento; eficiência computacional; requisitos de memória.
   **Características do algoritmo e da implementação:** Flexibilidade; adequação de hardware e software; simplicidade.

2. Qual foi o conjunto final de critérios usados pelo NIST para avaliar as cifras AES candidatas?

   Segurança geral, implementações de software, ambientes de espaço restrito, implementações de hardware, ataques a implementações, criptografia vs. descriptografia, agilidade de chave, outras versatilidades e flexibilidades e potencial para paralelismo em nível de instrução.

3. Qual é a diferença entre Rijndael e AES?

   Rijndael permite comprimentos de bloco de 128, 192 ou 256 bits.
   AES permite apenas um comprimento de bloco de 128 bits.

4. Responda:
   a) Qual é a finalidade do array Estado?

   O array Estado contém os resultados intermediários no bloco de 128 bits em cada estágio do processamento.

   b) Como é construída a S-box?

   1 - Inicializa a S-box com os valores de byte em sequência ascendente linha por linha. A primeira linha contém {00}, {01}, {02}, etc., a segunda linha contém {10}, {11}, etc., e assim por diante. Assim, o valor do byte na linha x, coluna y é {xy}.

   2 - Mapeia cada byte na caixa S para seu inverso multiplicativo no campo 8 finito GF(2⁸); o valor {00} é mapeado para si mesmo.

   3 - Considera que cada byte na caixa S consiste em 8 bits rotulados (b₇, b₆, b₅, b₄, b₃, b₂, b₁, b₀). Aplica a seguinte transformação a cada bit de cada byte na caixa S:
```math
b'_i = b_i \oplus b_{(i+4) \mod 8} \oplus b_{(i+5) \mod 8} \oplus b_{(i+6) \mod 8} \oplus b_{(i+7) \mod 8} \oplus c_i
```

onde *c* é o i-ésimo bit do byte *c* com o valor {63}; isto é, (c₇c₆c₅c₄c₃c₂c₁c₀) = (01100011). O (') indica que a variável deve ser atualizada pelo valor à direita.

c) Descreva rapidamente o estágio SubBytes, ShiftRows, MixColumns, AddRoundKey, e o algoritmo de expansão de chave.

**SubBytes:** Cada byte individual do Estado é mapeado em um novo byte da seguinte maneira: Os 4 bits mais à esquerda do byte são usados ​​como um valor de linha e os 4 bits mais à direita são usados ​​como um valor de coluna. Esses valores de linha e coluna servem como índices na S-box para selecionar um valor de saída exclusivo de 8 bits.

**ShiftRows:** A primeira linha do Estado não é alterada. Para a segunda linha, um deslocamento circular de 1 byte para a esquerda é executado. Para a terceira linha, um deslocamento circular de 2 bytes para a esquerda é executado. Para a terceira linha, um deslocamento circular de 3 bytes para a esquerda é executado.

**MixColumns:**  opera em cada coluna individualmente. Cada byte de uma coluna é mapeado em um novo valor que é uma função de todos os quatro bytes naquela coluna

**AddRoundKey:** Os 128 bits do Estado são submetidos a um XOR bit a bit com os 128 bits da chave redonda.

**Algoritmo de expansão de chave:** O algoritmo de expansão de chave AES toma como entrada uma chave de 4 palavras (16 bytes) e produz uma matriz linear de 44 palavras (176 bytes).

5. Quantos bytes em Estado são afetados por ShiftRows?

   12 bytes.

6. Use a chave 1010 0111 0011 1011 para encriptar o texto claro "ok" conforme expresso em ASCII, ou seja, 0110 1111 0110 1011. Os projetistas do S-AES obtiveram o texto cifrado 0000 0111 0011 1000. E você?

   **Expansão de chave:**

   W0 = 1010 0111

   W1 = 0011 1011

   W2 = 0001 1100

   W3 = 0010 0111

   W4 = 0111 0110

   W5 = 0101 0001

   **Rodada 0:**

   Depois de Add Round Key: 1100 1000 0101 0000

   **Rodada 1:**

   Depois da Transformação de subbytes: 1100 0110 0001 1001

   Depois de ShiftRows: 1100 1001 0001 0110

   Depois de Mix Columns: 1110 1100 1010 0010

   Depois de Add Round Key: 1110 1100 1010 0010

   **Rodada 2:**

   Depois da Transformação de subbytes: 1111 0000 1000 0101

   Depois de ShiftRows: 0111 0001 0110 1001

   Depois de Add Round Key: 0000 0111 0011 1000

7. Compare AES com DES. Para cada um dos seguintes elementos do DES, indique o elemento comparável no AES ou explique por que ele não é necessário no AES.

   a) XOR do material da subchave com a entrada da função f.

   AddRoundKey.

   b) XOR da saída da função f com a metade esquerda do bloco.

   A etapa de MixColumn, porque é aqui que os diferentes bytes interagem entre si.

   c) função f.

   A etapa de ByteSub, porque contribui com a não linearidade para o AES.

   d) permutação P.

   A etapa de ShiftRow, porque permuta os bytes.

   e) troca de metades do bloco.

   Não há troca generalizada de linhas ou colunas. O AES não exige esta etapa porque: A etapa de MixColumn faz com que cada byte em uma coluna altere todos os outros bytes da coluna, portanto, não há necessidade de trocar linhas; A etapa de ShiftRow move bytes de uma coluna para outra, portanto não há necessidade de trocar colunas.

8. (1 ponto-extra) Calcule a saída da transformação MixColumns para a seguinte sequência de bytes de entrada "67 89 AB CD". Aplique a transformação InvMixColumns ao resultado obtido para verificar seus cálculos. Altere o primeiro byte da entrada de "67"para "77", realize a transformação MixColumns novamente para a nova entrada e determine quantos bits mudaram na saída.
   Nota: você pode realizar todos os cálculos à mão ou escrever um programa que dê suporte a eles. Se escolher escrever um programa, ele deverá ser feito inteiramente por você; nesta tarefa, não use bibliotecas ou código fonte de domínio público (você pode se guiar pelos exemplos Sage
   disponibilizados).

9. (2 pontos-extra) Crie um software que possa encriptar e decriptar usando S-AES. Dados de teste: um texto claro binário de 0110 1111 0110 1011 encriptado com uma chave binária de 1010 0111 0011 1011 deverá dar o texto cifrado binário 0000 0111 0011 1000. A decriptação deverá funcionar da mesma forma.
