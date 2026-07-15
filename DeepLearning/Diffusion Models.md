### Ruído
Adição de ruído à n Imagens
Imagem + $\epsilon$
$$x_1 \leftarrow x_0\sqrt{1-\beta_1} + \epsilon \sqrt \beta_1$$
$$x_t \leftarrow x_{t-1}\sqrt{1-B_1} + \epsilon \sqrt B_1$$
onde $\epsilon \in N(0,I)$
### Treinamento
O treinamento é autosupervisionado e conduzido por correção de erro. Como as pertubações na imagem são geradas pelo modelo, ele conhece o erro real.
Onde a função de perda é definida da seguinte forma:$$L = E[|\epsilon - \epsilon_\theta(x_tt)|^2]$$

