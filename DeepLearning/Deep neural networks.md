Redes com mais de uma camada escondida de [[Perceptrons]]. Pode ser entendido como uma concatenação de redes rasas.
Sejam duas redes $y, y'$ com saídas:$$
\begin{aligned}
y = \phi_0 + \phi_1h_1 + \phi_2h_2 + \phi_3h_3 \\
y = \phi_0' + \phi_1'h_1' + \phi_2'h_2' + \phi_3'h_3'
\end{aligned}
$$
A concatenação desses dois modelos gera novas funções de decisão, uma rede rasa com a mesma quantidade de neurônios produzirá no máximo apenas 7 regiões com 19 parâmetros, em comparação aos 20 parâmetros e pelo menos 9 regiões da rede profunda. Isso torna essas redes capazes de representar mais regiões de decisão.
### Hyperparameters
A profundidade da rede é a quantidade de camadas da rede e a quantidade de unidades escondidas por camada é a largura da rede. Esses são os hiperparâmetros, escolhidos antes do treinamento da rede.


