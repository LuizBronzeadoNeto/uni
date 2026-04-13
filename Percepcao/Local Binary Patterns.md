É um descritor (como visto em [[Image representation and extraction]]) de textura. Imune a fontes de iluminação.
#### Conceito
Dividir a janela examinada em células e para cada pixel na célula, comparar o pixel com cada um dos seus 8 vizinhos, seguindo os pixels em um circulo.
Onde o centro tem o brilho maior que o vizinho, escreve-se 1, caso contrário, 0, terminando assim com um número de 8 bits. Deve-se então computar o histograma, por célula, da frequência de cada "número" que ocorre (opcionalmente pode-se normalizar esse histograma). 
Desse modo, dado um pixel $(x_c, y_c)$:
$$
LBP_{P}^{R} = \sum_{p=0}^{P-1} s(g_p - g_c)2^P
$$
Onde:
* r é o raio da vizinhança
* P é a quantidade de vizinhos
e:
$$
s(x) = \begin{cases}
1, & x \ge 0\\ 
0 &
\end{cases}
$$
Entretanto, quando há alguma interferência externa, esse algoritmo não funciona.
Um histograma LBP é mais discriminativo do que um histograma tradicional de brilho
##### Multi-scale Block LBP
É uma maneira de calcular áreas maiores com LBP, dividindo o "Block" em sub-blocks, dos quais são obtidos os valores binários, é essencialmente uma maneira de abstrair o resultado de um LBP normal.
