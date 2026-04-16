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
