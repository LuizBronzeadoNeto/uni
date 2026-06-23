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
Uma função de perda relevante as vezes não pode ser otimizada de forma eficiente. A solução é otimizar uma surrogate loss function que age como um proxy, que tem suas vantagens, permitindo o modelo estimar a probabilidade condicional das classes.
#### Funções
- $\text{NLL} = \sum -log(y_i)$
Devido ao formato do gráfico do logaritmo, ao negar o resultado do $log(y_i)$. Classificações errôneas ($\text{Loss} \rightarrow \infty$) serão penalizadas fortemente.
#### Algoritmos de minibatch
Otimização é iterativa em ML. Usando um conjunto de treinamento grande para toda iteração é computacionalmente inviável.
Algoritmos de minibatch utilizam, como o nome indica, apenas b exemplos em cada iteração onde $1 \leq b < m$.
Cada iteração pode ter baixa performance em relação à o batch completo, porém após múltiplas iterações, a performance torna-se comparável.
São eficientes em comparação ao full batch pois o erro padrão da média é computado por:$$\frac{\sigma}{\sqrt{n}}$$ Mostrando que os retornos são menos que lineares quanto mais exemplos.

### Saddle point
Para muitas funções não convexas de alta dimensionalidade, mínimos locais são casos raros. Mínimos locais devem satisfazer:$$
\begin{aligned}
\frac{\delta j}{\delta\theta_i} = 0,i = 1,n \\
\frac{\delta^2j}{\delta^2 \theta_i} = 0,i = 1,n
\end{aligned}
$$
### Algoritmos de aprendizagem básico
Seja $\epsilon$ a taxa de aprendizagem global
#### Stochastic gradient descent
É o algoritmo GD com aplicação de minibatch do conjunto de treinamento.
Gradiente: $$\hat{g} \leftarrow \frac{1}{m}V_0 \sum_i^m L(f(x^{(i)}; \theta) y^{(i)})$$
##### Momentum
Projetado para acelerar o aprendizado, acumula uma média móvel exponencialmente decadente de gradientes passados, continua a mover na direção da GD. No algoritmo a velocidade é acumulada $v_t \leftarrow \alpha v_{t-1} - \epsilon \hat{g}$ e a atualização é aplicada: $$\theta \leftarrow \theta + v_t$$
A ideia é atualizar mais rapidamente quando o gradiente é maior e menos quando o gradiente é pequeno.
##### Gradientes adaptativos (AdaGrad)
SGD modificado com uma taxa de aprendizado por parâmetro (lr), lr aumenta em parâmetros com gradiente pequenos, e decresce em parâmentros com gradientes largos
Gradientes quadrados acumulados: $$r \leftarrow r + g \odot g$$
aplicar atualização:$$\theta \leftarrow \theta -\frac{\epsilon}{\delta + \sqrt{r}}\odot g$$
##### RMSProp
Similar ao AdaGrad, porém usa gradientes quadrados modificados:$$r \leftarrow \rho r + (1 - \rho)g\odot g$$
##### Adam (momentos adaptativos)
Combinação de RMSProp e momentum.
Acumula primeira e segunda estimativas do momento$$
\begin{aligned}
s \leftarrow \rho_1 s + (1 -\rho)g \\
r \leftarrow \rho_2 r + (1 - \rho_2)g\odot g
\end{aligned}$$
Bias é normalizado:$$
\begin{aligned}
\hat s \leftarrow \frac{s}{1 - \rho_1^t} \\
\hat r \leftarrow \frac{r}{1 - \rho_2^t}
\end{aligned}$$
E por fim se aplica a atualização ao $\theta$:$$\theta \leftarrow \theta - \epsilon \frac{\hat s}{\sqrt{\hat r} + \delta}$$
O melhor algoritmo é determinado por análise empírica para os hiperparâmetros do conjunto de dados.
### Inicialização de parâmetros
A maioria dos algoritmos são fortemente afetados pela escolha de inicialização. Dois conjuntos de parâmetros convergentes com custo comparáveis podem ter erros de generalização muito diferentes (devido à alta complexidade do modelo).
Parâmetros iniciais precisam "quebrar a simetria" entre unidades diferentes, ou seja, duas unidades escondidas do mesmo tipo conectadas à mesma entrada precisam ter parâmetros inciais diferentes.
Biases para cada unidade são geralmente atribuídos de forma heurística, enquanto os pesos vem de uma distribuição randômica. A escala da distribuição inicial tem um grande efeito no resultado da otimização e na generalização.
#### Inicialização Xavier
Inicializar os pesos de uma camada completamente conectada (m inputs x n outputs)  guiados por uma distribuição uniforme$$U(-\frac{1}{m},-\frac{1}{m})$$
Pode levar a pesos pequenos caso a camada for grande. 
##### Inicialização esparsa
Cada unidade é inicializada para ter exatamente $k < m$ pesos não zero.
Isso previne que a magnitude de pesos individuais diminua com $m$ e ajuda a adquirir mais diversidade.
#### Batch normalization
Otimiza redes neurais profundas, porém não é um algoritmo de otimização, mas sim um método de reparametrização adaptativa. Soluciona desvio covariado. Normalizando a entrada de cada camada dado o minibatch.
##### BN transformation
Apenas normalizar cada entrada de uma camada pode mudar o que a camada pode representar. Para resolver isso, é preciso introduzir uma transformação linear para cada ativação.$$BN_{y, \beta} (x_{1...m}) = y \hat x_{1...m} + \beta$$
### Redes convolucionais
Para tarefas de alta-dimensionalidade, com grandes quantidades de dados de entradas, o uso de MLPs torna-se inviável.
Redes convolucionais (CNN) permitem o processamento de grandes dados de entrada. São ideais para processar dados com topologia similar a uma grade, onde convolução é utilizada ao invés de uma multiplicação de matriz em pelo menos uma camada.
Quando a entrada muda, a saída muda da mesma forma, por exemplo,$$I(x,y) = I)(x-1,y)$$
Se M for uma máscara convolucional e $\odot$ a operação convolucional:
$$ M \odot I' = I'(M \odot I)$$
