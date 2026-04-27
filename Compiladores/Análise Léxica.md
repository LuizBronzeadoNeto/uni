A primeira etapa do compilador, realizada pelo analisador léxico, que recebe um fluxo de caracteres e retorna um fluxo de tokens. (nome, **valor-atributo token**)
### Conceitos Básicos
(Programa fonte) ---> **Analisador Léxico** (getNextToken)<-->(token) **Analisador Sintático**

Um **token** é um par consistindo em um nome e um valor opcional. Um **padrão** é uma descrição da forma que os lexemas encontrados no código fonte de um token podem assumir, logo um token pode ter as seguintes formas:
* (Nome, _ )
* (Nome, Lexema)
* (Nome, Apontador para tabela de símbolos)
A especificação dos padrões vai ser feito por meio de expressões regulares (autômatos).
O analisador realiza a remoção de espaços em branco e comentários, correlaciona mensagens de erros com o programa fonte, inicia a construção da tabela de símbolos e realiza a expansão de macros.
```java
/*Exemplo de código*/\n
int x = 10    ;\n
```
Para produzir os tokens deste exemplo, primeiro será casado /* com o padrão de comentário, logo não se gera token.
Em seguinte se geram os tokens: **<tipo, int>, <id, 1>** (sempre que nome do token for um identificador, o seu valor será um apontador para a tabela de símbolos, que conterá uma linha com informações da variável, função etc: 1 | x | int |...) , **<opatrib, = >,<numero, 10>** (em caso de literais, o valor do token pode ser tanto o literal em si, ou um id para a tabela onde o literal está contido), **<SP, ;>** (espaços em branco removidos.
As vezes deve-se ler adiante antes de se determinar o token a ser construído, por exemplo: '<', '=', '<=', '-', '-='
### Buffers de Entrada
Devido ao grande número de caracteres para serem lidos em pouco tempo. Portanto, tornam-se necessárias técnicas especializadas.
#### Pares de Entradas
Dois buffers são carregados alternadamente com dois apontadores que são mantidos
![[Pasted image 20260415112228.png]]
Esse esquema exige 2 testes: Fim do Buffer e qual caractere foi lido.
#### Sentinelas
É possível combinar os dois testes dos pares de entradas fazendo uso de um caractere especial que não pode fazer parte do programa fonte
![[Pasted image 20260415112602.png]]
```java
switch (* forward++){
	case eof:
		if (forward está no fim do primeiro buffer){
			recarrega segundo buffer;
			forward = inicio do segundo buffer;
		}
		else if (forward está no fim do segundo buffer){
			recarrega primeiro buffer;
			forward = inicio do primeiro buffer;
		}
		else //eof dentro de um buffer marca o fim da entrada
			termina a análise léxica;
		break;
	Casos para outros caracteres
	}
}
```
### Especificação de Tokens
É necessário uma notação para especificar os padrões de lexemas. Desse modo, pode-se usar expressões regulares que já descrevem linguagens e portanto, são uteis no reconhecimento de padrões.
#### Cadeias 
Um alfabeto é qualquer conjunto finito de símbolos e uma cadeia é uma sequência finita de símbolos retirada desse alfabeto. Assim, uma linguagem é qualquer conjunto contável de cadeias de algum alfabeto fixo.
Na análise léxica existem 3 operações fundamentais:
* União: $$L \cup M = \{s|s \subset L \lor s \subset M\} $$
* Concatenação
* fecho de Kleene: $$ L^* = U_{i=0}^\inf L^i$$
#### Expressões regulares
Definem uma notação criada para descrever todas as linguagens que podem ser formadas a partir da aplicação de operadores fundamentais sobre os símbolos de um alfabeto


##### Definições regulares
se $\sigma$ é um alfabeto de símbolos básicos então uma definição regular é uma sequência de definições na forma:
$$ d_n \rightarrow r_n$$
exemplo: Números sem sinal
		digito --> 0 | 1 | ... | 9
		digitos --> digito digito*
		fracaoOpcional --> digitos | $\epsilon$
		expoenteOpcional --> (E(+|-) digitos) | $\epsilon$
		numero --> digitos fracaoOpcional expoenteOpcional
### Reconhecimento de Tokens
É preciso construir um trecho de código que examine a cadeia de entrada e encontrar um prefixo que seja um lexema casando com um dos padrões.
		stmt --> if (exp) then stmt
				 if (exp) then stmt else stmt
				 $\epsilon$
		 exp --> term relop term
				 term
		 term --> id
				 number
Padrões para esses tokens são descritos através de expressões regulares.
Padrões são convertidos em fluxogramas estilizados, chamados **diagramas de transição**, que possuem arestas direcionadas e rotuladas. Consideramos que todos os diagramas de transição são deterministas.
#### Diagramas de transição
Existem duas formas para lidar com palavras reservadas parecidas com identificadores
1. Cadastro de palavras reservadas na tabela de símbolos
2. Diagramas de transição separados para cada palavra reservada
#### Analisador Léxico baseado em diagrama de transição
Existem diferentes formas de usar uma coleção de diagramas de transição para construir um analisador léxico. Onde cada estado é representado por um trecho de código, com uma variável state contendo o número do estado corrente e uma variável switch baseado no valor do state.
A forma mais comum de se codificar um analisador léxico é combinar todos os diagramas em um.
```java
TOKEN getRelop(){
	TOKEN retToken = new (RELOP);
	while(1){
		switch(state) {
			case 0: c = nextChar();
				if (c == ‘<‘) state = 1;
				else if (c == ‘=‘) state = 5;
				else if (c == ‘>‘) state = 6;
				else fail();
				break;
			case 1: ...
			...
			case 8: retract();
		retToken.attribute = GT;
		return(retToken);
		}
	}
}
```

### Autômatos finitos
São grafos semelhates aos diagramas de transição, podendo ser de 2 tipos: Não deterministas e deterministas (NFA e DFA)
#### NFA
Um NFA consiste em um conjunto finito de estados S, um conjunto de símbolos de entradas $\Sigma$, um estado $s_0$ considerado o estado inicial e um subconjunto de estados $F$ finais.
Pode-se representar um NFA por um digrafo e por uma tabela de transição.
Um NFA aceita uma cadeia de entrada $x$ se houver algum caminho no grafo de transição do estado inicial para um estado final, de modo que todas as transições comportem $x$
#### DFA
Um DFA é um caso especial de NFA, onde não existem movimentos sob a entrada $\epsilon$ e para cada estado $s$ e símbolo de entrada $a$, existe exatamente uma aresta possível
#### Algoritmo MCNaughton-Yamada-Thompson
Um algoritmo composicional que recebe como entrada uma expressão regular $r$ sob o alfabeto $\Sigma$ e retorna um NFA $N$ aceitando $L(r)$.
Comece desmembrando $r$ em suas subexpressões constituintes, então aplique as regras BASE e de INDUÇÃO.
* BASE: para qualquer subexpressão $a$ em  $\Sigma$ e para a expressão $\epsilon$, construa o NFA
* INDUÇÃO: suponha que $N(s)$ e $N(t)$ sejam NFAs para as expressões regulares $s$ e $t$, respectivamente
	1.  Considere $r = s|t$, então, $N(t)$ é construído da seguinte forma:![[Pasted image 20260422111343.png]]
	2. Considere $r = st$, então, $N(t)$ é construído da seguinte forma: ![[Pasted image 20260422111459.png]]
	3. .  Considere $r = s*$, então, $N(s)$ é construído da seguinte forma:![[Pasted image 20260422111639.png]]
#### DFAs a partir de expressões regulares
Sabe-se que é possível transformar uma expressão regular em um autômato não determinista, logo, para transforma-la em um NFA, é preciso transformar esse DFA para um DFA
##### Construção de subconjuntos de um DFA a partir de um NFA
Operações sobre estados do NFA:
* $\epsilon$-closure(s) - conjunto de estados do NFA que podem ser alcançados a partir do estado s do NFA apenas sobre $\epsilon$-transições
* $\epsilon$-Closure(T) - conjunto de estados alcançáveis a partir de **qualquer estado do conjunto T** usando apenas $\epsilon$-transições.
* move(T,a) - Conjunto de estados do NFA para os quais existe uma transição sob o símbolo de entrada a.

```java
while (exoste i, estadp não marcado) 
{
	DTrans.addState(T);
	for (cada simbolo de entrada x){
		U = eClosure(move(T,x));
		if (u not in dataset)
			Inclui u como estado não marcado em DStates
		Dtran(T, x) = u;
	}
}
```
### Gerador de Analisador Léxico LEX
Permite especificar um analisador léxico definindo expressões regulares na linguagem lex:
	(programa fonte lex.l) --> Compilador LEX --> lex.yy.c
#### Estrutura de programas LEX
1. Declarações de variáveis, constantes e definições regulares
2. Regras de tradução
3. Funções auxiliares
O LEX e  o analisador sintático devem estar em sintonia, pois ele chama o analisador léxico, que lê a entrada até encontrar o maior prefixo que case com um dos padrões.

