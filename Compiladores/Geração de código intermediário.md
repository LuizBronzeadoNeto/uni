A etapa imediatamente após a [[Análise semântica]]. Ao chegar nesta etapa, o código não possui nenhum erro léxico, sintático ou semântico
### Gerador de código intermediário
Durante o processo de tradução entre duas linguagens, o compilador constrói e usa uma ou mais representações intermediárias (RI), que deve ser fácil de produzir e traduzir para código de maquina.
#### DAGs
Semelhantes às árvores de sintaxe, porém um nó N de um DAG pode possuir mais de um pai.

### Código de três endereços
Composto por um conjunto de endereços e instruções, onde existe no máximo um operador do lado direito da instrução.$$x+y+z$$ vira:$$\begin{aligned} t_1=y+z \\ t_2=x+t_1 \end{aligned}$$
Uma instrução pode ser uma atribuição, uma cópia, um desvio incondicional ($\text{goto}(L)$), um desvio condicional (if x goto(L)), chamadas de procedimentos, chamadas de função, um valor retornado, uma instrução indexada de cópia (x = y[i] e x[i] = y, ou seja, atribui a x o valor contido no endereço i unidades de memória além do endereço y, e virse-versa). 
#### Arranjo
base + I * W
Para duas dimensões $$\text{base} + i_1w_1 +i_2w_2$$ Onde $w_1$ é a largura de uma linha e $w_2$ é a largura de um elemento de uma linha.
Desse modo, para n dimensões$$\text{base} + i_1w_1+...+i_nw_n$$



