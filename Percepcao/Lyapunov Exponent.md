1O expoente de Lyapunov é uma métrica analítica que pode ajudar a caracterizar o caos, que mede o quão rápido uma distância infinitesamente pequena entre 2 pontos cresce pelo tempo:
$$
F^t(x_0 + \epsilon) - F^t(x_o) \approx \epsilon e^{\lambda t}
$$
F é a função de evolução do sistema dinâmico, o lado esquerdo é a distância entre dois estados incialmente próximos após $t$ iterações, enquanto o lado direito é a suposição que a distância cresce exponencialm2ente (caos). O expoente $\lambda$, medido por um grande período de tempo (idealmente $t \rightarrow \infty$ ), é o **expoente de Lyapunov**.
### Computação
É possível transformar essa fórmula numa versão mais facilmente computável:
$$
lim_{t \rightarrow \infty}{\frac{1}{t}} = \sum_{t = 0} ^{t - 1} log|\frac{dF}{dx}|_{x=x_i}
$$
O resultado final acaba sendo simples de computar numericamente: o expoente de Lyapunov é uma média temporal de $log|\frac{dF}{dx}|$ em todos os estados que o sistema visita ao longo da simulação.

```python
from pylab import *

def initialize():
	global x, result
	x = 0.1
	result = [logdFdx(x)]
def observe():
	global x, result
	result.append(logdFdx(x))
def update():
	global x, result
	x = x + r - x**2
def logFdx(x):
	return log(abs(1 - 2*x))
def lyapunov_exp():
	initialize()
	for t in xrange(100):
		update()
		observe()
	return mean(result)

```

