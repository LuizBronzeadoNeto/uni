Todo software deve ser escrito em uma linguagem de programação, esse software precisa ser traduzido de alguma forma para poder ser executado em computadores de arquiteturas diferentes, esse é o papel do **compilador**.
### Processadores de linguagens
O **compilador** traduz um programa escrito em uma linguagem, para outro programa escrito numa linguagem compreendida por um arquitetura de um computador. Caso seja encontrado algum erro durante esse processo, ele é relatado pelo compilador.
Um **interpretador** é outro tipo de processador de linguagem, ao contrário de produzir um programa destino como resultado de uma tradução, ele é outro programa que entende o original, ou seja, não realiza a tradução.
**Just-in-time compilers** (JIT) são uma abordagem híbrida que traduz o código enquanto o código original executa.

Outros programas podem ser necessários para que a linguagem seja processada corretamente, como por exemplo:
**Pré-processadores**: realiza o preprocessamento, como fetch de dados em outros arquivos (bibliotecas, classes etc) e pode criar macros.
**Assembler**:  Monta o código em assembly.
**Linker & Loader**: Editor de ligação e carregador, aloca e carrega o código na memória.
### A estrutura de um compliadores
A tarefa de um compilador pode ser divida em duas etapas básicas **Análise**, **Síntese**
A **análise** quebra o programa fonte em pedaços e lhe impõe uma estrutura gramátical, a partir da qual cria uma representação intermediária.
A **síntese** produz o programa destino.
#### Fases de um compilador
(_Fluxo de caracteres_) -> **Análisador léxico** ---> (_Fluxo de tokens_) -> **Analísador Sintático** ----> (_Árvore Síntatica_) -> **Análisador Semântico** ---> (_Árvore Síntatica_) -> **Gerador de Código Intermediário**  ---> (Representação intermediário) -> **Otimizador de código independente** ---> (Representação intermediária) -> **Gerador de código** ---> (Código de máquina destino) -> **Otimizador de Código Dependente de Maquina**
##### Análise léxica
Primeira fase do compilador, recebe como fluxo de entrada de caracteres do programa de entrada e os agrupa em lexemas, que são sequências significativas de caracteres. Para cada lexema, o analisador léxico produz como saída um token (**<--- questão de prova**) na forma:
						(nome do token, **valor**)
Exemplo:
```java
pos = ini + avg * 60
```
gera:
<id, 1> \<=\>, <id, 2>, <+>, <id, 3>, <\*>, <60>
Para lexemas de palavras reservadas como while, pode-se reduzir <while, while> para apenas < while >
##### Análise sintática
A análise léxica gera uma árvore baseado numa gramática livre de contexto
##### Análise Semântica
Checa a consistência semântica do programa fonte a partir da árvore sintática e da tabela de símbolos, além de checagens adicionbais sobre a sintaxe da linguagem.
#### Tabela de símbolos
Estrutura de dados que permite guardar informações sobre as entidades do programa fonte:
- Nome
- Tipo
- Endereço de memória
- número. nome e tipos de argumentos
- Tipo de passagem de parâmetro
- Tipo de retorno