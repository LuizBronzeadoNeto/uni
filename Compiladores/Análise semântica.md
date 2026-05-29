### Esquema de tradução dirigido por sintaxe
É uma gramática livre de contexto acrescida de atributos e regras. Atributos são associados aos símbolos da gramática e regras à produções. Se $X$ é um símbolo e $a$ um de seus atributos, $X.a$ denota o valor de $a$ em um determinado nó da árvore de derivação rotulado com $X$.
#### Atributo Sintetizado
Para um não-terminal $A$ em um nó $N$ de derivação é definido por uma regra semântica associada à produção daquele nó.
Os atributos podem ser associados aos símbolos das gramáticas. Regras podem descrever como calcular esses atributos nas árvores de derivação.
Um atributo sintetizado pode ser definido em termos dos valores dos atributos herdados do próprio nó $N$.
#### Atributo Herdado
Para um não-terminal $B$ em um nó $N$ da árvore de derivação é definido por uma regra semântica associada à produção no Pai de $N$.
Um atributo herdado no nó $N$ não pode ser definido em termos dos valores dos atributos dos seus filhos.
Os elementos terminais da gramática podem ter atributos sintetizados, mas não atributos herdados. Não existem regras semânticas na DDS para computar o valor de um atributo para um terminal

