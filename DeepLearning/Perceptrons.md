Desenvolvidos por Rosemblat, são a rede mais simples para classificação de padrões linearmente separáveis. Utiliza o modelo McCulloch-Pitts de [[Intro to Neural Nets]].
Função de ativação
* $a_t(t+1) = f(u_i(t))$$$a_i(t+1)= \begin{cases}
1 & u(t) < 0 \\ 
0 & u(t) \ge 0
\end{cases}$$
onde u:$$u = \sum{x_j}{w_j} - \theta$$
Possui duas camadas, uma camada de pré-processamento com M máscaras fixas para extração de características com pesos fixos e outra de discriminação com presos determinados através de aprendizado.
O treinamento é realizado de forma supervisionada, com correção de erro:
* $\Delta w_{ij} = \eta x_i(d_j - y_j)$        $d \neq y$
* $\Delta w_{ij} = 0$        $d = y$ 
#### Teorema da Convergência
Se é possível classificar um conjunto de entradas, uma rede Perceptron fará a classificação.
### Multi Layer Perceptrons
Redes de uma camada resolvem apenas problemas linearmente separáveis. A solução é utilizar mais de uma camada, ex:
* Camada 1: uma rede perceptron para cada grupo de entradas linearmente separáveis
* Camada 2: uma rede combina as saídas das redes da primeira camada, produzindo a classificação final.
Cada camada computa uma função linear, que é composta.
A função de ativação não deve ser linear de modo a ser capaz de produzir redes que representem mapeamentos complexos, devendo informar os erros para camadas anteriores:
* Função sigmoide
* Função tangente hiperbólica
* ReLU
#### Redes Multi-Layer Perceptron
É a arquitetura de RNA mais utilizada. O seu treinamento pode ser realizado por uma grande variedade de algoritmos, geralmente supervisionados, como **estáticos** (que não alteram a estrutura da rede) e **construtivos** (que alteram a estrutura).
##### Backpropagation
Um tipo de treinamento estático. A rede é treinada com pares I/O, cada entrada de treinamento está associada a uma saída desejada, o treinamento é realizada em duas fases, cada percorrendo em um sentido (Forward, backward).
Funcionamento do algoritmo:$$E = \frac{1}{2} \sum_j(d_j-y_j)²$$
Erro para um padrão, considerando todos os nodos de saída.$$\Delta w_{ji} \Join - \frac{\delta E}{\delta w_{ji}}$$
O peso é ajustado com sinal contrário ao mínimo




