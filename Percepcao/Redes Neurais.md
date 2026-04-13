#### Perceptrons
São camadas escondidas que armazenam uma representação abstrata interna dos dados. Uma rede pode ter mais de uma camada escondida. Entretanto, um número maior de camadas leva a 2 problemas: **Vanishing Gradients** e **Overfitting**.
##### Autocodificadores
É tipicamente uma rede neural feedfoward, a rede é treinada para "recriar" a entrada.
É possível criar uma rede que consiste de vários **autocodificadores empilhados**, a camada oculta do autoencoder t atua como a camada de entrada para o autoencoder t + 1, com a primeira camada atuando como a entrada da rede.
Com essa arquitetura, é possível reusar representações quando os componentes são suficientemente similares.
