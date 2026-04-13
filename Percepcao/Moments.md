Relacionado a [[Image representation and extraction]]
Existem 3 tipos de momentos.
* Hu moment
* R moment
* Zernike moment
seja $I$ uma imagem e $f$ uma função de imagem o nth momento digital $(p, q)$ é dado pela seguinte fórmula:
$$
m_{pq}(I) = \sum_{(x, y) \in I}x^p y^qf(x, y)
$$
O $(p,q)$ momentos centrais de $I$ podem ser definidos como:
$$
\mu_{pq}(I) = \sum_{(x, y) \in I}(x-x_0)^p(y-y_0)^q f(x, y)
$$
Onde:
* $x_0 = \frac{m_{10}}{m_{00}}$
* $y_0 = \frac{m_{01}} {m_{00}}$
Os momentos centrais normalizados de $f$ são dados por:
$$
\eta_{pq} = \frac{\mu_{pq}}{\mu_{pq}^{\gamma}}
$$
Onde $\gamma =\frac{p+q}2 + 1$
Momentos de Hu são invariantes a translação, escala e rotação (RST).
3Momentos de R melhoram a escala e invariabilidade dos momentos de Hu.

