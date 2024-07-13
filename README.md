# ECC_Ed25519
Elliptic Curve Cryptography (ECC) with curve 25519 using GNU Multi-Precision Library (GMP) 

/*____________________________________________________________________________
Code developed by Iago Lucas (iagolbg@gmail.com | GitHub: iagolucas88)
for his master's degree in Mechatronic Engineering at the
Federal University of Rio Grande do Norte (Brazil).

Elliptic Curve Cryptography (ECC) for IoT devices
(microcontrollers) implementing Curve25519 (Daniel J. Bernstein).
____________________________________________________________________________*/

Para utilizar o progama, necessita instalar a biblioteca GMP. Complila-se com g++ com o comando abaixo (onde 'ECC_Ed25519.CPP' e 'ECC_Ed25519' são os arquivos do código e o MAKE.file, respectivamente):

$ g++ -I /usr/local/include -L /usr/local/lib -L /lib ECC_Ed25519.CPP -o ECC_Ed25519 -lgmp -lm -pthread

$ ./ECC_Ed25519


INICIALIZAR E GERAR CHAVES

1. Recebe a mensagem com quaisquer caracter;
2. Codifica a string para um mpz_t;
3. Garante que a mensagem possui mais dígitos que o p (primo);
4. Gera a chave privada (necessita de uma semente confiável e um state) que é o 'k' (escalar) necessário para 'mult_escalar';
5. A chave pública (P3) é gerada pela chave privada usando a operação de multiplicação escalar de pontos (k vezes) na curva elípitica (começa no ponto inicial). Apenas faz-se necessário armazenar a coordenada x deste ponto, pois pela equação de Ed25519, calcula-se a coordenada y;
6. Ultiliza-se o método ADD-DOUBLE-POINT que, a partir das equações de Edwards para curva 25519, realiza a adição e duplicação de pontos nesta curva (Montgomery Curve);
7. Com a mensagem codificada e a chave pública, encripta a mensagem;
8. Com a mensagem encriptada e a chave privada, decripta a mensagem;
9. Descodifica a mensagem (apenas o inteiro da coordenada x) para a string original.
