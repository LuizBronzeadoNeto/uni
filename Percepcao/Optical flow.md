É a [[Percepção do Movimento]] aparente de objetos da imagem entre 2 frames consecutivas onde cada vetor é um vetor de deslocamento representando o movimento de pontos da primeira frame à segunda.

![[Pasted image 20260203173404.png]]
A seta na imagem representa o vetor de deslocamento.
O fluxo óptico assume 2 coisas:
1. As intensidades dos pixeis de um objeto não mudam entre frames consecutivos
2. pixeis vizinhos possuem movimento similar
Considere um pixel $I(x, y, t)$ na primeira frame, dada a distância $(dx,dy)$ a próxima frame é tomada após $dt$ tempo, portanto pode-se dizer que:
$$I(x, y, t) = I(x + dx, y+dy, t+dt)$$
Pegando a aproximação de séries de Taylor da direita e removendo os termos em comum e dividindo por $dt$, tem-se a equação do fluxo óptico:
$$f_xu +f_yv +f_t = 0$$
onde:
$$f_x=\frac{\delta f}{\delta x};f_y = \frac{\delta f}{\delta y}$$
$$u = \frac{dx}{dt};v=\frac{dy}{dt}$$
