#### Vídeo Estéro
A diferença entre posições de objetos em 2 imagens tiradas de fontes próximas é chamada de **disparidade**, ou seja, a discrepância angular na posição de um objeto projetada nos dois olhos.
Visão estéreo é a medição dessa disparidade. A forma mais simples e conveniente de representar e armazenar medidas de profundidade de uma cena é através de um mapa de profundidade, que é um array bidimensional onde as informações de distância $x$ e $y$ correspondem às linhas e colunas do array, e as medições correspondentes de profundidade $z$ são armazenadas como elementos do array.
Para calcular a posição $(x, y ,z)$ de um objeto numa imagem onde este objeto tem coordenadas $(x_l', y_l')$ e $(x_r', y_r')$, onde $f$ é a distância focal de ambas as câmeras e $d$ a distância entre elas:
$$
\frac{x_l'}{f} = \frac{x+\frac{1}{2}d}{z}
$$
$$
\frac{x_r'}{f} = \frac{x-\frac{1}{2}d}{z}
$$
$$
\frac{y_l'}{f} = \frac{y}{z}
$$
Portanto, segue:
$$
x= \frac{d(x_l'+x_r')}{2(x_l'-x_r')}
$$
$$
y= \frac{d(y_l'+y_r')}{2(x_l'-x_r')}
$$
$$
z= \frac{df}{2(x_l'-x_r')}
$$
