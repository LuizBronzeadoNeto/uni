Para garantir a integridade, segurança, privacidade etc. Se usa mecanismos de segurança como criptografia, autenticação, monitoramento, etc.
### Onde implementar Mecanismos
Princípio e2e: depender de uma camada intermediária para uma garantia que somente os extremos conseguem verificar completamente. Aplicações tomam conta de sua segurança, reduzindo TCB (tudo aquilo que precisa ser confiado para a aplicação funcionar).
Esse princípio não reduz a necessidade de defesa em profundidade.

### Criptografia simétrica
Um algoritmo criptográfico é simétrico quando a chave usadas para criptografar ($E_x$) os dados, é a mesma para descriptografa-los ($D_x$). Ajuda a prevenir ataques passivos e ativos.
Deve haver uma maneira segura de trocar uma chave.
No caso de um compromentimento da chave, todos os dados são comprometidos.
#### Codificação
Codificação não é a mesma coisa que criptografia. Criptografia torna a informação ilegível para não autorizados, codificação muda a forma como a informação é transmitida ou armazenada.

#### AES
Família de cifras "Rijndael"
É uma família popular de algoritmos, usado em TLS e para criptografia de arquivo, mensagens e disco. É uma cifra de bloco, mas pode ser usada como de fluxo.
Usando o mesmo bloco básico para criptografia de bloco podemos ter vários modos de uso:
* Electronic Code Book
* Cipher Block Chaining
* Counter Mode
* Galois Counter Mode
* ...
Esses modos podem ser usados em qualquer cifra de bloco autorizada.
#### Modos AES
##### AES-ECB
(deprecado)
A entrada quebrada em blocos é criptografada individualmente usando a chave. Acaba sendo inseguro devido aos blocos deterministicos.
Se existe um mapeamento fixo entre entrada e saída, caso seja descoberta alguma informação sobre a entrada, informações em comum entre entradas posteriores serão iguais.
##### AES-CBC
Um modo mais adequado: a entrada é dividia em blocos e criptografada usando a chave e um Initialization Vector ou a chave e o resultado do bloco anterior. O IV pode ser público.
A desvantagem desse modo é que devido ao encadeamento, não é possível paralelizar o processo de (des)cifragem.
Foi deprecado por problemas diversos, como a complexidade da implementação, a falta de proteção de integridade e vulnerabilidade contra ataques de padding.
##### AES-CTR
Gera um fluxo contínuo de bytes pseudoaleatórios e combina-os com a entrada. O vetor de inicialização (aqui um nonce) quebra os padrões.
Reusar os IVs e chaves no modo CTR é muito pior que antes, se você tem uma mensagem sobre a qual você conhece o texto plano e o cifrado, ao fazer or XOR da mensagem criptografada com texto plano os bits
### Criptografia Assimétrica
O uso de duas chaves tem um grande impacto nas áreas de confidencialidade. A criptografia assimétrica foi o primeiro avanço realmente revolucionário, sendo baseada em operações matemáticas e não em operações de bits.
Ex.: A criptografia é realizada com a chave pública, enquanto os dados podem ser descriptografados apenas com a chave privada.
#### Propriedades desejadas
Deve ser fácil criar os pares de chaves e (des)criptografar mensagens. Por outro lado, deve ser difícil que adversários que tenham chave pública derivem a chave privada (muito menos a mensagem original).
Melhor ainda se ambas as chaves possam ser usadas para ambos os processos.
#### Troca de chaves
A criptografia assimétrica é um processo caro computacionalmente, para resolver esse problema, existem alguns algoritmos que usam criptografia assimétrica para combinar uma chave simétrica (que é a chave usada para criptografar os dados).
Um desses algoritmos é o algoritmo Diffie-Hellman.
### Algoritmos
#### RSA
Inventado em 1977, é uma cifra de bloco, texto plano e o cifrado são inteiros (entre 0 e m-1 mod m):
$p=3,q=11$
$n=pq, n=33$
$$\phi(n)=mmc((p-1),(q-1)), \phi(n)=20$$ escolha um co-primo $e$ (ex: 7) e calcule d tal que:
$$(de) \mod \phi(n)=1$$
$d=3$
$PR_k=(d,n) = (3, 33)$
$PU_k=(e,n) = (7,33)$
##### Computação homomórficas com RSA
Permite que operações sejam feitas em cima de dados criptografados devido ao homomorfismo parcial (não inclui adição) presente no RSA.$$C(m_1m_2)=C(m_1)C(m_2)$$
### Algoritmos pós-quânticos e híbridos
NIST padronizou em agosto de 2024:
* ML-KEM: encapsulamento de chaves (substitui X25519/RSA para troca de chaves)
* ML-DSA: assinaturas digitais
* SLH-DSA: assinaturas baseadas em hash
Uma solução popular pela falta de maturidade do PQC é combinar 2 algoritmos.

### Proteção de integridade
Geralmente um hash
Dado um Hash H:
* $H$ pode ser aplicado a um bloco de qualquer tamanho
* $H$ produz uma saída de calcular
* $H(x)$ deve ser fácil de calcular
* Para qualquer hash $h$, é inviável encontrar x a partir de $H(x)=h$
* Para qualquer texto $x$, é inviável achar y != x que $H(x) = H(y)$
* É inviável achar qualquer par $(x,y)$ tal que $H(x)=H(y)$ (resistência contra colisões)
O hash é a impressão digital de qualquer ativo digital e não "pode" ser forjado
#### Segredo de autenticação de mensagem
O Hash é calculado com base na mensagem + segredo (k), desse modo, mesmo que a mensagem seja modificada e o hash recalculado, como k não é incluso no transporte, um atacante não saberá como calcular o hash corretamente e durante a comparação, é possível identificar modificação.
O segredo também é incluso no início da mensagem, forçando qualquer atacante a recalcular o hash da mensagem inteira em cada tentativa (ao invés de só o final).
Também funciona para criptografia assimétrica, com chaves públicas e privadas.

#### Bloom filter
Usa funções de hash para determinar posições de um vetor de bits ativadas, para cada elemento, o número de bits ativos será o número de funções hash utilizadas. Para testar a presença de um elemento, calcula-se os seus hashes, então se verifica se todos os bits estão ativos.
### Criptografia e Perfect forward secrecy
O uso de PKI permite que mesmo que os certificados sejam comprometidos, dados trocados entre clientes no passado não serão comprometidos.
