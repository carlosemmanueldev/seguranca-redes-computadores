﻿# Segurança de Redes de Computadores

## :page_with_curl: Atividade 3

1. Responda os questionamentos a seguir:

   a) Por que é importante estudar a cifra de Feistel?

   A maioria dos algoritmos de criptografia de bloco simétrico em uso atualmente são baseados na estrutura de cifra de bloco de Feistel. Portanto, um estudo da estrutura Feistel revela os princípios por trás dessas cifras mais recentes.

   b) Qual é a diferença entre uma cifra de bloco e uma cifra de fluxo?

   Uma cifra de fluxo é aquela que criptografa um fluxo de dados digitais em um bit ou um byte de cada vez. Uma cifra de bloco é aquela em que um bloco de texto claro é tratado como um todo e usado para produzir um bloco de texto cifrado de igual comprimento.

   c) Por que não é prático usar uma cifra de substituição reversível qualquer do tipo mostrado na Tabela 3.1?

   Se um tamanho de bloco pequeno, como *n= 4*, for usado, então o sistema é equivalente a uma cifra de substituição clássica. Para *n* pequeno, tais sistemas são vulneráveis ​​a uma análise estatística do texto claro. Para um tamanho de bloco grande *n*, o tamanho da chave, que é da ordem de *n×2*, torna o sistema impraticável.

   d) O que é uma cifra de produto?

   Em uma cifra de produto, duas ou mais cifras básicas são executadas em sequência de tal forma que o resultado ou produto final seja criptograficamente mais forte do que qualquer uma das cifras componentes.

   e) Qual é a diferença entre difusão e confusão?

   Na difusão, a estrutura estatística do texto claro é dissipada em estatísticas de longo alcance do texto cifrado. Isto é alcançado fazendo com que cada dígito do texto claro afete o valor de muitos dígitos do texto cifrado, o que equivale a dizer que cada dígito do texto cifrado é afetado por muitos dígitos do texto claro.
   A confusão procura tornar a relação entre as estatísticas do texto cifrado e o valor da chave de criptografia tão complexa quanto possível, novamente para frustrar as tentativas de descobrir a chave. Assim, mesmo que o invasor consiga controlar as estatísticas do texto cifrado, a maneira como a chave foi usada para produzir esse texto cifrado é tão complexa que torna difícil deduzir a chave. Isto é alcançado através do uso de um algoritmo de substituição complexo.

   f) Que parâmetros e escolhas de projeto determinam o algoritmo real de uma cifra de Feistel?

   **Tamanho do bloco:** tamanhos de bloco maiores significam maior segurança (sendo todas as outras coisas iguais), mas velocidade de criptografia/descriptografia reduzida.

   **Tamanho da chave:** um tamanho de chave maior significa maior segurança, mas pode diminuir a velocidade de criptografia/descriptografia.

   **Número de rodadas:** A essência da cifra Feistel é que uma única rodada oferece segurança inadequada, mas múltiplas rodadas oferecem segurança crescente.

   **Algoritmo de geração de subchave:** Maior complexidade neste algoritmo deve levar a maior dificuldade de criptoanálise.

   **Função redonda:** Novamente, maior complexidade geralmente significa maior resistência à criptoanálise.

   **Criptografia/descriptografia rápida de software:** Em muitos casos, a criptografia é incorporada em aplicativos ou funções utilitárias de forma a impedir uma implementação de hardware. Consequentemente, a velocidade de execução do algoritmo torna-se uma preocupação.

   **Facilidade de análise:** Embora gostaríamos de tornar o algoritmo o mais difícil possível de criptoanalisar, há um grande benefício em tornar o algoritmo fácil de analisar. Ou seja, se o algoritmo puder ser explicado de forma concisa e clara, será mais fácil analisar esse algoritmo em busca de vulnerabilidades criptoanalíticas e, portanto, desenvolver um nível mais alto de garantia quanto à sua força.

   g) Explique o efeito avalanche.

   O efeito avalanche é uma propriedade de qualquer algoritmo de criptografia, de modo que uma pequena alteração no texto claro ou na chave produz uma alteração significativa no texto cifrado.

3. Qual(is) dos recursos abaixo estão presentes no projeto da rede de Feistel? Explique.

   a) Tamanho do bloco e da chave;

   b) Função da rodada;

   c) Gerador de sub-chaves;

   **d) Todas as alternativas.**

   Todas as alternativas estão corretas. A rede de Feistel utiliza o tamanho do bloco e da chave, uma função da rodada, e um gerador de sub-chaves para criar uma sequência de rodadas de cifragem, cada uma mais complexa e difícil de reverter sem a chave correta.

4. Qual é o tamanho do texto claro no Data Encryption Standard (DES)? Explique.

   a) 57;

   b) 48;

   c) 32;

   **d) 64.**

   O DES divide o texto claro em blocos de 64 bits antes de aplicar o processo de criptografia. Cada bloco de 64 bits passa por 16 rodadas de operações, como permutações, substituições e a aplicação da função de Feistel. Embora a chave usada tenha 64 bits, apenas 56 bits são efetivamente utilizados (os outros 8 bits são usados para paridade).

5. A cifra de Feistel do algoritmo de encriptação utilizada no Data Encryption Standard (DES) utiliza quantos S-boxes? Explique.

   **a) 8;**

   b) 7;

   c) 6;

   d) 5.

   O DES utiliza 8 S-boxes para realizar substituições durante o processo de encriptação. Essas S-boxes mapeiam blocos de 6 bits de entrada para 4 bits de saída, ajudando a criar confusão e dificultar a reversão do texto cifrado para o texto claro.

6. O Data Encryption Standard possui uma chave de 56 bits, o que torna possível um espaço de 2⁵⁶ chaves possíveis. Essa sentença trata de ataque de. . . Explique.

   a) Tempo;

   b) Matemático;

   **c) Força-Bruta;**

   d) DoS.

   No caso do DES, que utiliza uma chave de 56 bits, existem 2⁵⁶ chaves possíveis. Um ataque de força-bruta tenta todas essas combinações até encontrar a chave que decripta o texto cifrado. Como o DES tem um espaço de chaves relativamente pequeno para os padrões atuais, é vulnerável a esse tipo de ataque, pois o poder computacional moderno pode testar grandes quantidades de chaves em um tempo viável.

8. Demonstre, através de um exemplo, como realizar a cifragem de 16 bits (dois caracteres), em 2 rounds, em seguida, decifre o texto cifrado. Explique o processo passo a passo. Forneça um código Python/Sagemath com sua solução.

9. Considere uma cifra de Feistel composta de 16 rodadas com tamanho de bloco de 128 bits e tamanho de chave de 128 bits. Suponha que, para determinado *k*, o algoritmo de escalonamento de chave defina valores as oito primeiras chaves de rodada, k1, k2, . . . , k8, e depois estabeleça

   $$k9 = k8, k10 = k7, k11 = k6, . . . , k16 = k1$$

   Admita que você tenha um texto cifrado S. Explique como, com acesso a um oráculo de encriptação, você pode decriptar *c* e determinar *m* usando apenas uma única consulta a ele. Isso mostra que tal cifra é vulnerável a um ataque de texto claro escolhido. (Um oráculo de encriptação pode ser imaginado como um dispositivo que, dado um texto claro, retorna o texto cifrado correspondente. Os detalhes internos do dispositivo não são conhecidos, e você não pode abri-lo. Você só consegue obter informações do oráculo fazendo consultas a ele e observando suas respostas.)

   No ataque de texto claro escolhido, podemos explorar a repetição das chaves *(k9 = k8​, k10=k7k​, etc.)* para simplificar o processo de descoberta da chave ou do texto claro. Nesse caso, uma única consulta ao oráculo permite que se submeta um texto claro escolhido e observe como ele é encriptado. Com base nessa resposta, pode-se decriptar o texto cifrado e obter o texto claro *m*.
   Esse ataque é possível porque a repetição das chaves reduz a complexidade do ataque, permitindo que o atacante obtenha informações suficientes com apenas uma consulta.
