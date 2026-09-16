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

