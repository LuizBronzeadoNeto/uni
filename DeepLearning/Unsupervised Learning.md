Modelos que não baseiam seus treinamentos no ajuste de pesos com base em uma função de perda.
### Estratégia comum
Definir um mapeamento entre exemplos x e variáveis latentes não-vistas z, onde z captura a estrutura essencial do dataset (geralmente com dimensão menor que x).
O mapeamento entre variáveis observadas e latentes pode ser em ambas as direções.
### Taxonomia de treinamento não-supervisionado
#### Características de um bom modelo generativo
* Efficient sampling
* High-quality sampling
* Coverage
* Well-behaved latent space
* Disentangled latent space
* Efficient likelihood computation
### Adversarial Networks (GANs)
Aprendem a gerar exemplos x levando como base representações latentes z. Conforme o treinamento progride, os exemplos gerados passam a ficar cada vez menos distinguíveis de exemplos reais.
Duas redes são treinadas, um gerador, que gera as amostras, e um discriminador, cuja tarefa é distinguir objetos reais de objetos gerados pela rede geradora.

### Variational Autoencoders
Diferente de autoencoders tradicionais, autoencoders variacionais possuem uma propriedade adicional no espaço latente, a Completude. Ou seja, qualquer ponto amostrado do espaço latente deve produzir conteúdo significativo quando decodificado.

