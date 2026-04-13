#### Detecção do movimento
##### Subtração simples
A técnica mais simples para detecção de movimento é a **subtração simples de background**, que funciona mantendo um modelo do background estático, comparando o quadro corrente com o background a fim de destacar regiões de movimento no foreground e [[Pattern Recognition]]. [[Image representation and extraction]], [[Moments]]
O modelo do background é uma imagem estática (presume-se que não há objetos presentes). Pixels são rotulados como movimento (1) ou como não movimento(0) com base num limiar das diferenças absolutas de itensidade entre os quadros.
```python
B(0) = I(0)
...
for t in time:
	I(t) = next_frame()
	diff = abs[B - I(t)]
	M(t) = threshold(diff, lambda)
	...
	B(t) = I(t)
```
Desse modo, objetos que entram na cena e param continuam a ser detectados, dificultando a detecção de novos objetos que passam na frente deles.
O método é também sensível à alteração da iluminação e ao movimento sem importância do fundo.
##### Diferença entre quadros
Outro método seria a diferença entre quadros, onde o modelo de background é substituido pelo quadro anterior:
```python
B(0) = I(0)

for t in time:
	I(t) = next_frame()
	diff = abs[B(t - 1) - I(t)]
	M(t) = threshold(diff, )
	...
	B(t) = I(t)
```
Uma versão melhorada desse método é a **diferenciação de 3 quadros**, primeiro deve-se definir a escala temporal:
$$D(N) = |I(t) - I(t + N)|$$
Diferente da diferença entre quadros adjacentes, é possível bufferizar os quadros, tornando a silhueta mais completa, porém possui acuracia reduzida. Desse modo na diferença entre 3 quadros, se interpola a posição do objeto num movimento -x (onde ele estava + onde ele está agora) e +x (onde ele está agora + onde ele passará a estar) para ter-se o objeto no momento presente:
##### Subtração adaptativa
É um método que é mais sensível às mudanças na iluminação e no movimento da câmera.
```python
B(0) = I(0)

for t in time:
	I(t) = next_frame()
	diff = abs[B(t - 1) - I(t)]
	M(t) = threshold(diff, )
	...
	B(t) = alpha*I(t) + (1 - alpha)*B(t-1)
```
##### Diferenciação Persistente de Quadros
Áreas de movimento são combinadas com um termo de decaimento linear.
Imagens de histórico de movimento
```python
B(0) = I(0)
R(0) = 0
for t in time:
	I(t) = next_frame()
	diff = abs[B(t - 1) - I(t)]
	M(t) = threshold(diff, )
	tmp = max[H(t - 1) - y, 0]
	H(t) = max[255*M(t), tmp]
	...
	B(t) = I(t)
```
#### Rastreamento de blobs
A determinação da correspondência entre blobs ao longo dos quadros é baseada na similaridade de caracteristicas (localização, tamanho / forma, velocidade ou/e aparência)
