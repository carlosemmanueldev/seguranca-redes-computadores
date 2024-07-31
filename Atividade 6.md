# Segurança de Redes de Computadores

## :page_with_curl: Atividade 6

1. O que é encriptação tripla?
Com a criptografia tripla, um bloco de texto claro é criptografado passando-o por um algoritmo de criptografia; o resultado é então passado pelo mesmo algoritmo de criptografia novamente; o resultado da segunda criptografia é passado pelo mesmo algoritmo de criptografia uma terceira vez. Normalmente, o segundo estágio usa o algoritmo de descriptografia em vez do algoritmo de criptografia.

2. O que é ataque meet-in-the-middle?
Este é um ataque usado contra um algoritmo de criptografia dupla e requer um par conhecido (texto claro, texto cifrado). Em essência, o texto claro é criptografado para produzir um valor intermediário na criptografia dupla, e o texto cifrado é descriptografado para produzir um valor de intermediação na criptografia dupla. Técnicas de consulta de tabela podem ser usadas de tal forma a melhorar drasticamente uma tentativa de força bruta de todos os pares de chaves.

3. Quantas chaves são usadas na encriptação tripla?
A criptografia tripla pode ser usada com três chaves distintas para os três estágios; alternativamente, a mesma chave pode ser usada para o primeiro e o terceiro estágios.

4. Por que a parte do meio do 3DES é decriptação, em vez de encriptação?
Não há significância criptográfica para o uso de descriptografia no segundo estágio. Sua única vantagem é que permite que usuários do 3DES descriptografem dados criptografados por usuários do DES único mais antigo repetindo a chave.

5. Por que alguns modos de operação de cifra de bloco só utilizam a encriptação, enquanto outros empregam encriptação e decriptação?
Em alguns modos, o texto claro não passa pela função de criptografia, mas é XORed com a saída da função de criptografia. A matemática faz o trabalho para a descriptografia nesses casos, a função de criptografia também deve ser usada.

6. Você deseja construir um dispositivo de hardware para realizar encriptação de bloco no modo cipher block chaining (CBC) usando um algoritmo mais forte do que DES. 3DES é um bom candidato. A Figura 1 mostra duas possibilidades, ambas acompanhando a definição do CBC. Qual das duas você escolheria:
	a) Por segurança?
	Se os IVs forem mantidos em segredo, o caso de 3 loops terá mais bits a serem determinados e, portanto, será mais seguro do que o de 1 loop para ataques de força bruta.

	b) Por desempenho?
	Para implementações de software, o desempenho é equivalente para a maioria das medições. Um loop tem dois XORs a menos por bloco. Três loops podem se beneficiar da capacidade de fazer um grande conjunto de blocos com uma única chave antes de alternar. A diferença de desempenho da escolha do modo pode ser esperada como menor do que as diferenças induzidas pela variação normal no estilo de programação. Para implementações de hardware, três loops são três vezes mais rápidos do que um loop, por causa do pipelining. 

7. Crie um software que possa encriptar e decriptar no modo cipher block chaining usando uma das seguintes cifras: módulo affine 256, módulo Hill 256, S-DES, DES. Teste os dados para S-DES usando um vetor de inicialização binário de 1010 1010. Um texto claro binário de 0000 0001 0010 0011 encriptado com uma chave binária de 01111 11101 deverá dar um texto claro binário de 1111 0100 0000 1011. A decriptação deverá funcionar de modo correspondente.
