#### Circuitos Resistivos simples
Circuitos em que a distribuição dos resistores é comparativelmente simples
##### Resistores em série
Pela lei das correntes de Kirchhoff, pode-se deduzir que, quando existe um circuito com resistores em série, ao se conhecer uma das correntes, se conhece todas as correntes que passam nos resistores.
Além disso, pela lei das tensões, pode-se deduzir que, como a tensão total será a corrente vezes a resistência equivalente de todos os resistores [[Introduction to Circuits]]
$$
v = i_sR_{eq}
$$
O cálculo da resistência equivalente em resistores em série será:
$$
R_{eq} = \sum_{i = 1}^{k}R_i = R_1 + R_2 +... + R_k
$$
Pode-se utilizar essa informação para simplificar um circuito, afinal, outro maneira de pensar na resistência equivalente é como uma caixa preta, se um circuito tem 4 resistores de $5\Omega$ conectados em série ou apenas um resistor de $20\Omega$ o resultado é o mesmo.
##### Resistores em paralelo
A caracteristica definidora de um circuito em paralelo é que eles devem ter a mesma tensão entre si. Logo, mesmo se no diagrama os resistores estão em "paralelo", eles ainda podem estar conectados de outra forma
Novamente, usando a mesma lógica anterior, pode-se reduzir a Resistência de vários resistores em paralelos para um resistência equivalente usando a lei das correntes de Kirchhoff e a lei de Ohm:
$$
\frac{1}R_{eq} = \sum_{i = 1}^{k}\frac{1}R_i = \frac{1}R_1 + \frac{1}R_2 +... + \frac{1}R_k
$$
Perceba que o resultado dessa equação é a condutância equivalente, logo ela pode ser reescrita como:
$$
G_{eq} = \sum_{i = 1}^{k}G_i = G_1 + G_2 +... + G_k
$$
##### Circuitos divisores de tensão
Muitas vezes é necessário haver mais de uma tensão a partir de uma única fonte em um circuito eletrônico, e existem circuitos com essa exata finalidade
![[Pasted image 20251208164010.png]]
Neste caso, sabemos pela lei das correntes de Kirchhoff que $R_1$ e $R_2$ conduzem a mesma corrente, logo pela lei das tensões:
$$
v_1 + v_2 - v_s = 0 \rightarrow v_s = v_1 + v_2
$$
$$
v_s = iR_1 + iR_2
$$
$$
i = \frac{v_s}{R_1 + R_2}
$$
Assim, usando a lei de Ohm, é possível calcular as tensões $v_1$ e $v_2$:
$$
v_1 = iR_1 = R_1 \frac{v_s}{R_1 + R_2}
$$
$$
v_2 = iR_2 = R_2 \frac{v_s}{R_1 + R_2}
$$
Essas equações ilustram claramente que tanto $v_1$ quanto $v_2$ são frações de $v_s$, e como o resultado dessas frações sempre é menor que 1, ambas são menores que $v_s$.
##### Circuitos divisores de corrente
Consiste em dois resistores ligados em paralelo:![[Pasted image 20251208172511.png]]
para determinar suas correntes aplica-se a lei de Ohm e a lei das correntes de Kirchhoff em paralelo:
$$
i_1 = i_s \frac{R_2}{R_1 + R_2}
$$
$$
i_2 = i_s \frac{R_2}{R_1 + R_2}
$$
A fórmula não muda para quantidades maiores de resistores, sendo feita em etapas
##### Divisão de Tensão e de Corrente
Com essas equações em mãos, é possível generaliza-las em técnicas chamadas como divisão de tensão e corrente. Dado um circuito com uma tensão $v$, quer se saber a queda de tensão $v_j$ num resistor qualquer $R_j$, sabe-se que:
$$
i = \frac{v}{R_{eq}}
$$
Logo, para calcular a queda de tensão:
$$
v_j = v\frac{R_j}{R_{eq}}
$$
Similarmente, para calcular a queda de corrente:
$$
i_j = \frac{R_{eq}}{R_j}i
$$


#### Técnicas de Análise de circuitos
Antes de prosseguir, é necessário definir nomenclatura:
* Nó essencial: um nó onde 3 ou mais elementos de um circuito se juntam
* Caminho: uma trilha por sobre elementos básicos sem passar mais de uma vez pelos elementos
* Ramo: um caminho que liga 2 nós
* Ramo essencial: um caminho que liga 2 nós essenciais sem passar por outro nó essencial
* Malha: um laço que não engloba nenhum outro laço
##### Transformação de fontes

Uma transformação de fonte permite que uma fonte de tensão em série com um resistor seja substituida por uma fonte de corrente em paralelo com o mesmo resistor, que possuirá corrente:
$$
i = \frac{v_s}R
$$
