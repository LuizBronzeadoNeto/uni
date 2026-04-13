#### MFCC
A escala do mel é uma escala de tons que a audição humana geralmente percebe como equidistantes uma das outras.
A medida da frequência aumenta, o intervalo, em hertz. O espectrograma mel remapeia os valores em hertz para a escala de mel, é ideal para aplicações que precisam modelar a percepção auditiva humana, como o [[Reconhecimento De Fala]].
Os coeficientes que compões um vetor de caracteristicas MFCC são resultantes da transformada discreta de cosseno (DCT) sobre o espectrograma mel.
![[Pasted image 20260213152851.png]]
##### Contraste Espectral
Cada quadro $(\delta t,\delta f)$ de um espectrograma $S$ é dividido em sub-bandas, para cada sub-banda, ordenam-se os componentes de frequência em ordem descendente. O contraste de energia é estimado comparando-se a energia média com a energia no quartil superior com a do quartil inferior.
##### Tonnetz
É um diagrama conceitual que representa, com o nome sugere, uma rede de tons


