Um dos grandes interesses de procesammento de imagens é reconhecimento de objetos. A fim de, por exemplo descrever regiões baseadas em representações e descrições.
Representação torna informações de objetos mais acessíveis para interpretação.
#### Description
Descrição é quando quantificamos a representação do objeto, podendo ser dividida em:
##### Boundary Descriptors
* Geometrical descriptors: diameter, perimeter, eccentricity, curvature
* Shape numbers
* Fourier descriptors
* Statistical Moments
##### Regional Descriptors
* Texture
* Moments of 2D functions
* Area, compactness, Euler number

Descrições possuem propriedades desejadas: eles devem ser um conjunto completo e compacto, ou seja, se 2 objetos tem a mesma forma, eles devem ter a mesma descrição, caso contrário, eles devem conter informações apenas sobre o que os deixas únicos. Eles devem ser invariantes a operações (RST).
Além disso, eles devem ser robustos, trabalhando bem contra Noise e distorções enquanto mantendo uma complexidade computacional relativamente baixa.
Por exemplo, a teoria do Momento, funciona bem em imagens normais, porém não tão bem imagens binárias.

Logo Feature extraction é o processo pelo qual áreas de interesse de imagens são detectadas e extraidas para processamento.

---

#### Feature Vectors
Um vetor de caracteristicas é um array $n * 1$ que guarda n elementos de uma determinada feature, matemáticamente, um vetor de caracteristicas é definido como:
$$
x =\{x_1, x_2, ..., x_n\}^T
$$
ou seja, é uma representação compacta de uma imagem.
Invariancia RST garante que um sistema de visão de maquina zainda conseguirá reconhecer objetos independente dessas operações.

##### Binary Object features
Um objeto bínario é uma região conectada dentro de uma imagem binária $f(x, y)$ que será denotada como $O_i , i > 0$.
$$
O_i(x, y) = \begin{cases}
1 & f(x, y) \in O_i\\ 
0 &
\end{cases}
$$
##### Chain code
Etapas para construção de chain codes:
- Selecionar um ponto inicial da fronteira e o representar por suas coordenadas absolutas na imagem
- Representar todo ponto consecutivo por um chain code mostrando a transição necessária para ir do ponto atual ao próximo ponto na fronteira
- Parar se o próximo ponto é o _ponto inicial_ ou o _fim da fronteira_
O código de freeman é uma maneira de calcular o chain code usando 8 direções de expansão possíveis.
Quando o chain code para uma fronteira foi computado, é possível converter o array resultante a um equivalente rotação-invariante, conhecido como a **primeira diferença**. 
A primeira diferença é obtida pelo encoding do número de mudanças de direções, expressos em múltiplos de 90°
##### Algoritmos para obter shape number
1. Obter o eixo maior da forma e considera-lo como um dos eixos de coordenadas
2. Encontrar o retângulo básico
3. Subdividir à ordem de n esse retângulo
4. Aplicar o código de chain code
#### Signatures
É uma representação unidimencional polar de uma boundary. Considere que uma figura tem o seu centro de massa, dada essa coordenada central, se traça um raio a um ponto na superfice do objeto, então se altera o ângulo do raio em relação a sua posição a superfice do objeto usando esse raio, alterando seu comprimento.
Assinaturas são invariantes à localização, mas dependem da **rotação** e **escala**.

##### Medial Axis Transform (MAT)
O MAT de uma região R com uma fronteira B é definida como: para todo ponto p de R, encontramos os seu vizinho mais próximo em B, se R tem mais de um desses pontos, ele pertence ao eixo esqueleto da imagem ou medial axis

---

#### Histogram-based features
Também referidas como caracteristicas de amplitude, o descritor mais simples é a média de valores de cinza de uma imagem, a vantagem de muitas dessas features é sua invariância a transformações RST da imagem:
$$m=\sum_{j=0}^{L-1} r_jp(r_j) $$
onde $r_j$ é o o nível de cinza j de um total de L valores possível cuja probabilidade de ocorrência é $p(r_j)$.
O desvio padrão do brilho (dispersão em torno da média) é dado por:
$$\sigma = \sqrt{\sum_{j=0}^{L-1} (r_j - m)²p(r_j)}$$
O skew (simetria da imagem), é um momento de terceira ordem, que mede a assimetria de distribuição de intensidades, ele é dado por:
$$
skew = \frac{1}{\sigma³}\sum_{j=0}^{L - 1}(r_j-m)³p(r_j)
$$
pode-se também calcular a entropia:
$$entropy = -\sum_{j=0}^{L-1} p(r_j)log_2[p(r_j)] $$
A entropia e a energia da imagem tendem a variar inversamente em uma imagem.

#### Texture based features
Rugosidade, smoothness e outros tipos de texturas numa imagem podem ser poderosos identificadores de caracteristicas em imagens.
##### Haar-like features
São descritores de visuais baseados em diferenças de intensidades entre regiôes retangulares de uma imagem. São calculados como a diferença entre a soma dos pixels em áreas claras e escuras definidas por retângulos adjacentes, podem ser usadas na captura de padrões simples como bordas, linhas e mudança de textura
Algo chamado **imagem integral** pode ser utilizada para acelerar o cálculo dessas features, pois ela guarda o valor da diferença do brilho de pixeis adjacentes, como essa diferença é utilizada para o cálculo de haar-like features, o processo é acelerado.