### Gerador de Código
Mapeia uma representação intermediária do programa fonte para o código na linguagem destino
Se a linguagem destino for código de máquina, registradores e posições de memória são selecionados para cada varável contida no programa fonte.
O gerador de código possui requisitos rígidos:
- Preservar o significado semântico do programa fonte;
- Ser de alta qualidade;
- O próprio gerador precisa ser executado eficientemente.
#### Seleção da instrução
Complexidade do mapeamento é determinada pelo nível da RI, a natureza da arquitetura alvo e a qualidade desejada do código final.
Endereços de memória são necessários em assembly, diferente da RI.$$ x = y + z$$
vira:
```asm
67: LD R0, y
75: ADD R0, R0, z
83: ST x, R0
```
Otimizações no código (código morto, redundâncias, etc) depende dos grafos de fluxo na [[Otimização]].
#### Alocação e atribuição de registradores
Uma tarefa difícil na geração de código devido ao número limitado de registradores. 
Instruções possuem ordens de avaliação, exigindo menos registradores que outras
### Linguagem Objeto
Template: Rótulo, Operador, destino, operandos
Uma instrução pode ser:
- Carga (`LD dst, addr`)
- Armazenamento (`ST addr, r`)
- Computações (`Op dst, src1, src2 ,..., srcN`)
- Desvio incondicional (`BR L`)
- Desvio condicional (`Bcond r, L`)
Modos de endereçamento:
- Nome (x)
- Endereço indexado (x(r)) onde x(r) = conteúdo(a + conteúdo(r))
- Inteiro indexado por registrador (`LD R1, 100(R2)`)
### Custos de Programa e Instrução
Associar custos à compilação do programa.
Cada instrução possui um custo associado:$$C = 1 + C_\text{modo de endr}$$
```
x = a[i] + 1

100: MULT R2, i, #4
108: ADD R3, a(R2), #1
116: ST x, R3

x = a[i] + b[j]

100: MULT R2, i, #4
108: MULT R3, j, #4
116: ADD R4, a(R2), b(R3)
124: ST x, R4

a[i] = x - 1


100: MULT R2, i, #4
108: SUB R3, x, #1
116: ST a(R2), R3

```