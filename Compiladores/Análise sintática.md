A sintaxe de uma linguagem de programação descreve a forma apropriada de seus programas, formas comuns de representar tal sintaxe são gramáticas livre de contexto ou BNF (estas ajudando na tradução de um programa e na análise semântica.
A análise sintática recebe tokens da [[Análise Léxica]] e tenta montar uma árvore de derivação através da gramática usando algoritmos de análise sintática.
### Gramáticas
Gramáticas possuem regras de estruturação da linguagem (ou de produção). Ela é composta por elementos terminais (if, (, ), {, }, else) e elementos não-terminais (variáveis que representam sequências de terminais e/ou não-terminais, ou seja, aparecem pelo menos uma vez na cabeça de um nó de produção).
		**com --> if "(" expr ")" "{" com "}" else "{" com "}"
		com --> while (" expr ") "{" com "}"**
Uma gramática livre de contexto possui 4 componentes
- Um conjunto de símbolos terminais
- Um conjunto de símbolos não terminais
- Um conjunto de produções
- Designação de um símbolo inicial da gramática
Exemplo de gramática para expressões contendo operações de adição e subtração
		**lista --> lista + digito
		lista --> lista - digito
		lista --> digito
		digito --> 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9**
* Não terminais: lista e dígito
* terminais: + - 0 1 2 3 4 5 6 7 8 9
Os corpos das 3 produções com mesma cabeça podem ser agrupados de forma equivalente:
**lista --> lista + digito | lista - digito | digito**
#### Derivações
Uma gramática deriva cadeias. As produções são tratadas como regras de reescrita, começando com o símbolo inicial e substituindo repetidamente um não-terminal pelo corpo de uma produção para esse não-terminal. Exemplo:
		E --> E + E | E * E | -E | ( E ) | id
Se E representa uma expressão, então -E também deve representar uma expressão, a substituição de um único E por -E é descrita por: **E ==> -E**

Se S => $\alpha$, onde S é o símbolo inicial da gramática G, dizemos que $\alpha$ é uma forma sentencial de G, uma sentença de G é uma forma sentencial sem não terminais. A linguagem gerada por uma gramática é o seu conjunto de sentenças.
Uma linguagem que pode ser gerada por uma gramática é dita livre de contexto. No exemplo anterior, a cadeia -(id + id) é uma sentença da gramática:
		E => -E => -(E) => -(E + E) => -(id + E) => -(id + id)
**A análise sintática consiste em, a partir de uma cadeia de terminais, tentar descobrir como derivá-la a partir do símbolo inicial da gramática. Caso não possível, informar o(s) erros**
### Árvores de derivação
Para ver o relacionamento entre derivações e árvores de derivação, considere as regras base e de indução a seguir:
* Base: A árvore para $\alpha_1$ = A é um único nó rotulado como A
* Indução: suponha que já tenhamos construído uma árvore de derivação com $a_{i - 1}$. Suponha que $\alpha_i$ seja derivado de $\alpha_{i-1} = X_1 ... X_j$, substituindo $X_j$ um não terminal, por $\beta$.
Da esquerda para direita, as folhas de uma árvore formam o _resultado_ da árvore.
### Ambiguidade
Se duas árvores de derivação são possíveis para uma cadeia de uma gramática, essa gramática é considerada ambígua.
Deve-se gerar gramáticas sem ambiguidade para compilar aplicações ou utilizar métodos para reduzir a ambiguidade, por exemplo: uma gramática para expressões aritméticas pode ser construída a partir de uma tabela mostrando associatividade entre operações:
			expr --> expr + termo | termo
			termo --> termo * fator | fator
			fator --> id | (expr)
Nesse caso, um fator é uma expressão que não pode ser desmembrado por um operador.
Pode-se generalizar essa ideia para quaisquer n níveis de precedência. Para isso, precisamos de n + 1 não terminais; o primeiro, como fator, nunca pode ser desmembrado.
### Recursão à esquerda
Uma gramática possui recursão à esquerda se ela tiver um não-terminal A tal que exista uma derivação A => $\alpha$A para alguma cadeia $\alpha$.
Os métodos de análise descendente não podem tratar esse tipo de gramática.
* Recursão à esquerda imediata: A -> $\alpha$ | $\beta$
* Pode-se resolver: A -> $\beta$A' onde A' é um novo não terminal A' -> $\alpha$A' | $\alpha$
Esse procedimento elimina toda a recursão à esquerda das produções de A e A' (desde que nenhum $\alpha$ seja $\epsilon$), mas não a elimina para derivações em 2 ou mais passos.
#### Fatoração à esquerda
Nem sempre a escolha entre duas ou mais alternativas de produções é clara, a fatoração é a reescrita das produções para clarificar as alternativas.
Em geral, se A -> $\alpha \beta_1$ | $\alpha\beta_2$ forem produções-A
Para cada não terminal A, encontre o prefixo $\alpha$ mais longo, comum a duas ou mais regras,Se $\alpha \neq \epsilon$, substitua todas as produções A.