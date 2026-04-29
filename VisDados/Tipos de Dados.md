### Estética
Todas as visualizações de dados mapeiam valores de dados em recursos quantificáveis do gráfico resultante. Independente do tipo, todas as visualizações podem ser descritas com uma linguagem comum, que retrata como os dados se transformam em tinta no papel ou em pixels na tela.
A estética descreve todos os aspectos de um determinado gráfico, como texto, formas, posição, cor etc.  Desse  modo, ela também divide os dados em 2 grupos: contínuos ou discretos.
Assim, a estética é inteiramente dependente dos tipos de dados como:
* Números
* Categorias
* Datas
* Coordenadas
* Texto
#### Mapeamento
A **escala** define um mapeamento único entre dados e estética, uma escala precisa ser 1:1, do contrário, gera ambiguidade.
### Tipos
Variáveis são usadas para representar os dados que podem ser:
1. **Dados quantitativos**: Numéricos, variáveis geralmente são chamadas de _atributo_ ou _medida_.
2. **Dado qualitativo**: Categóricos, geralmente chamadas de _fatores_, podem ser ordenadas ou não.
### Escalas
Necessárias para qualquer tipo de visualização de dados.
#### Escalas de posição
Determinam onde estão os diferentes valores de dados. O mais utilizado é o sistema de coordenadas cartesianas (que possui uma escala linear).
Quando cada eixo representa uma unidade distinta, é possível esticar ou comprimir sem retirar a validade dos dados (entretanto não é recomendado quando os eixos x e y possuem a mesma unidade de medida, as linhas da grade devem formar quadrados perfeitos).
##### Escalas de posição não lineares
A mais comum é a escala logarítmica, muito útil com dados obtidos por meio de multiplicação ou divisão
#### Escalas de cor
Existem 3 casos de uso fundamentais para uso de cores:
1) Distinguir grupos de dados
2) Representar valores de dados
3) Destacar dados
Os tipos de cores e a maneira como são usadas variam em cada caso.
##### Escala de cor qualitativa
Usada para distinguir itens/grupos discretos entre si. Cores são escolhidas para parecerem distintas umas das outras, mas sendo equivalentes entre si. Além disso, nenhuma cor deve se destacar em relação a outra ou criar uma interpretação de ordem.
##### Escala de cor quantitativa
Para representar valores, a melhor escolha é a escala sequencial, que diferencia valores maiores/menores, ou próximos/distantes. A escala precisa variar uniformemente em toda a sua faixa.
A escala também pode ser divergente, composta de 2 sequenciais unidas a um ponto médio comum.
##### Escala de cor de destaque
Escala de cor acentuada, usada para enfatizar elementos relevantes para a história contada. A escala precisa possuir um conjunto de cores suaves e outro contendo cores mais fortes para o destaque, não é recomendado que sejam do mesmo tom de cor (pode levar a confusão).