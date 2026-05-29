### Aprendizagem vs otimização pura
Machine learning age de forma indireta, enquanto algoritmos de otimização focam apenas na otimização da própria função de custo.
O objetivo de machine learning é reduzir o erro de generalização esperado (risco). Entretanto, algoritmos de aprendizagem reduzem custos de funções (risco empírico)
### Minimização de risco empírico
$$J^*(\theta) = E_{(x,y) P_{data}}L(f(x;\theta),y)$$
A expectativa é tomada sobre a verdadeira distribuição de dados.
* Se ela é conhecida -> problema de otimização
* Se a distribuição verdadeira é desconhecida, mas um conjunto de amostras de treinamento é conhecida -> problema de machine learning
Um problema de machine learning pode ser convertido de volta para um problema de otimização, minimizando a loss esperada no conjunto de treinamento (risco empírico)
### Surrogate Loss function
Uma fumção de perda relevante as vezes não pode ser otimizada de forma eficiente. A solução é otimizar uma surrogate loss function que age como um proxy, mas tem suas vantagens.
#### Funções
- $\text{NLL} = \sum -log(y_i)$
#### Algoritmos de minibatch
Otimização é iterativa em ML. Usando um conjunto de treinamento grande para toda iteração é computacionalmente inviável.
Algoritmos de minibatch utilizam, como o nome indica, apenas b exemplos em cada iteração onde $1 \leq b < m$.
Cada iteração pode ter baixa performance em relação à o batch completo, porém após múltiplas iterações, a performance torna-se comparável.
### Saddle point
Para muitas funções não convexas de alta dimensionalidade, mínimos locais são casos raros. Mínimos locais devem satisfazer:$$
\begin{aligned}
\frac{\delta j}{\delta\theta_i} = 0,i = 1,n \\
\frac{\delta^2j}{\delta^2 \theta_i} = 0,i = 1,n
\end{aligned}
$$
