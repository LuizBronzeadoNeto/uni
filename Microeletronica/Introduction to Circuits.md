### Variáveis de circuitos
#### Tensão e corrente
A carga é Bipolar, o que significa que efeitos elétricos são descritos em termos de + e -. Além disso ela existe em quantidades discretas, que são múltiplos inteiros da carga eletrônica, $1.6022 * 10⁻¹⁹$.
Na teoria dos circuitos, a separação entre cargas dá origem a uma força (tensão) e a um fluxo (corrente).
##### Tensão
Tensão é a energia por unidade de carga criada pela separação:
$$v = \frac {dw} {dq} $$
onde:
* v = a tensão em **Volts**
* w = a energia em **joules**
* q = a carga em **coulombs**
##### Corrente
A corrente é dada como a variação da carga no tempo:
$$i = \frac{dq}{dt} $$
onde: 
* i = a corrente em **amperes**
* t = ao **tempo**
* q = a carga em coulombs
#### Elemento Básico ideal
O elemento básico ideal de circuito possui 3 atributos,
1. apenas 2 terminais
2. é descrito matemáticamente em termos de corrente e tensão
3. não pode ser subdividido

![[Pasted image 20251206145106.png]]
Desse modo, pode-se estabelecer uma relação entre corrente em carga Como já temos a equação para corrente, pode-se derivar:
$$ dq = \frac {di} {dt} $$
portanto:
$$q(t) = \int_{0}^{t} i(x)dx$$
Além disso, O diagrama do circuito permite ver a polaridade (que define qual fórmula de potência se usará)
#### Potência e Energia
##### Potência
A potência pode ser definida como:
$$p = \frac {dw} {dt}$$
onde:
* p = a potência em **Watts**
* w = a energia em **joules**
Assim, 1 Watt equivale a 1 Joule/segundo
Com essa definição pode-se derivar a **equação da potência**:
$$p = vi$$
No diagrama do circuito, a fórmula que deve ser usada para potência depende, como falando anteriormente, da polaridade:
![[Pasted image 20251206150721.png]]
Se $p>0$ ocorre absorção de potência pelo circuito, caso contrário, o circuito fornece potência.

---

### Elementos de circuitos
Os circuitos são compostos por vários elementos que exercem diferentes funções que contribuem para o resultado esperado (e para soluciona-los).
#### Fontes
Fontes de circuitos podem ser divididas em: fontes independentes ou dependentes, além disso, podem ser ideais ou não (geram de forma constante)
##### Fontes independentes e dependentes
Indepententes estabelecem uma tensão ou corrente de forma que não seja dependente de outros pontos do circuito, enquanto fontes dependentes, como o nome sugere, fazem o oposto
![[Pasted image 20251206151604.png]]
A tensão fornecida $v_s$, ou corrente fornecida $i_s$, para cada as fontes ideais do terceiro quadro é determinada de diferentes formas:
(a) $v_s = \mu v_x$ se for uma fonte de tensão com controle de **tensão**
(b) $v_s = \rho i_x$ se for uma fonte de tensão com controle de **corrente**
(c) $i_s = \alpha v_x$ se for uma fonte de corrente com controle de **tensão**
(d) $i_s = \beta v_x$ se for uma fonte de corrente com controle de **corrente**

#### Resistência Elétrica
Resistência é a capacidade de um matérial de impedir o fluxo de corrente, e segue a lei de Ohm:
$$v = iR $$
alternativamente (i:$- \rightarrow +$):
$$v = -iR $$
onde:
* v = a tensão
* i = a corrente
* R = a resistencia em **Ohms**
O inverso da resistência elétrica é chamado de condutância (mais sobre, vide [[transcondutancia]]), medido em Siemens:
$$ G = R⁻¹$$
Para expressar a potência nos terminais do resistor, pode-se:
1. utilizar a equação da potência $p = vi$
2. Expressar a potência em termos da **corrente** e resistência: $p = i²R$
3. Expressar em termos de **tensão**: $p = \frac {v²} {R}$
4. Em alguns casos o valor do resistor pode ser dado em termos da **condutância**, logo para calcular: $p = v²G$ ou $p = \frac {i²}{G}$

#### Leis de Kirchhoff

Diz-se que um circuito está resolvido quando, a tensão nos terminais de cada elemento e corrente que flui por ele foram determinadas. A lei de Ohm é importante para derivar essas soluções, porém nem sempre suficiente.
Para usar as leis de Kirchhoff, é necessário identificar os nós. Um **nó** é um ponto em um circuito onde 2 ou mais elementos se unem.
##### Lei das Correntes de Kirchhoff
A primeira Lei de Kirchhoff, também conhecida como a lei das correntes diz que:
* **A soma algébrica de todas as correntes em qualquer nó de um circuito é igual a 0**
$$
i_1 \pm i_2 \pm ...\pm i_n = 0
$$Em qualquer circuito com $n$ nós, $n - 1$ equações independentes podem ser derivada da leis das correntes de Kirchhoff. E por elas, é possível derivar a próxima lei de Kirchhoff
##### Lei das Tensões de Kirchhoff
Antes de formalmente definir formalmente a segunda lei de Kirchhoff, deve-se definir primeiro o que é um caminho fechado ou **laço**. Começando a partir de qualquer nó arbitrariamente escolhido, traça-se um caminho fechado correndo um trajeto que passa por todos os elementos básicos de circuitos selecionados e volta ao nó original sem passar por qualquer nó intermediário mais de uma vez.
Com isso, pode-se agora formalmente definir a segunda lei:
* **A soma algébrica de todas as tensões ao longo de qualquer caminho fechado em circuito é igual a 0**
$$
v_1 \pm v_2 \pm ...\pm v_n = 0
$$
Dese modo, pela lei de Ohm:
$$
iR_1 \pm iR_2 \pm ...\pm iR_n = 0
$$