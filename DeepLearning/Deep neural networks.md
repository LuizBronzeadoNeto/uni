Redes com mais de uma camada escondida de [[Perceptrons]]. Pode ser entendido como uma concatenação de redes rasas.
Sejam duas redes $y, y'$ com saídas:$$
\begin{aligned}
y = \phi_0 + \phi_1h_1 + \phi_2h_2 + \phi_3h_3 \\
y = \phi_0' + \phi_1'h_1' + \phi_2'h_2' + \phi_3'h_3'
\end{aligned}
$$
A concatenação desses dois modelos gera novas funções de decisão, uma rede rasa com a mesma quantidade de neurônios produzirá no máximo apenas 7 regiões com 19 parâmetros, em comparação aos 20 parâmetros e pelo menos 9 regiões da rede profunda. Isso torna essas redes capazes de representar mais regiões de decisão.
### Hyperparameters
Hiperparâmetros são propriedades de alto-nível para o modelo (define capacidade ou complexidade de um modelo).
A profundidade da rede é a quantidade de camadas da rede e a quantidade de unidades escondidas por camada é a largura da rede. Esses são os hiperparâmetros, escolhidos antes do treinamento da rede.
### Backpropagation
A Função de ativação de modelos profundos é não linear, diferenciável, contínua e geralmente, não decrescente. Exemplo:
Sigmoidal logística:$$a_i(t+1) = \frac{1}{1+e^{u_i(t)}}$$
O ponto de partida para o algoritmo de backpropagation é obter a expressão de ajuste de pesos:$$\begin{aligned}
		E = \frac{1}{2}\sum_j(d_j-y_j)² \\
		\Delta w_{ji} \Join -\frac{\delta E}{\delta w_{ji}}
		\end{aligned}
		$$
A partir desta ideia, fazendo manipulações matemáticas, obtemos a expressão de ajuste$$\delta_j(t)= \begin{cases} (d_j - y_j)f'(net), & node=output \\ (\sum_j \delta_iw_{ij})f'(net_j), & else \end{cases}$$
Em cada iteração o algoritmo realiza duas fases:
* Foward (a rede gera suas saídas a partir de suas entradas)
* Backwards (a rede ajusta seus pesos a partir de suas saídas)
### Regularização
Regularização é qualquer modificação realizada para prevenir overfitting, sendo possível controlar a performance de um algoritmo (reduz o erro de teste, porém não o erro de treinamento).
Exemplo, decaimento de pesos para problema da regressão$$j(w) = MSE_{train} + \lambda w^t w$$

