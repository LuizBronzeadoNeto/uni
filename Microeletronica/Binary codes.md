#### Binary Coded Decimal (BCD)
Neste código cada dígito decimal é representado por um número binário de 4 digitos:
* 1: 0001
* 8: 1000
* 9: 1001
* 5: 0101
* 17: 00010111 (1 7)
#### Gray code (Reflected binary code)
Dois valores sucessivos se diferenciam com **apenas um bit**. Números binários são usados na conversão para gray code.
#### Checksum
dividir a mensagem em blocos e somá-los, como estamos realizando a soma em complemento de 1, caso haja carry over no final, deve-se fazer um wrap around na soma (se o resultado for 10100 onde 10 é o carry over no final, deve-se fazer 100 + 10). Depois disso, deve-se tirar o complemento de 1 do resultado (no exemplo: 110 vira 001), então o checksum é appended à mensagem.
O receiver então recebe a mensagem e soma todos os blocos, incluindo a checksum, se o resultado for composto por apenas 1s: aceitar; caso contrário, rejeitar.

