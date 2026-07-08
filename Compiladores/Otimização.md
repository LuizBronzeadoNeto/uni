### Blocos Básicos
Geração de código se beneficia do contexto. Blocos básicos são sequências de instruções consecutivas de 3 endereços que satisfazem algumas propriedades:
* O fluxo de controle só entra no bloco básico por meio da primeira instrução
* O controle sairá do bloco sem interrupção ou desvio, exceto possivelmente na última instrução.
Os blocos básicos formam nós em um grafo de fluxo.
#### Regras para encontrar líderes:
1. A primeira instrução de 3 endereços no código é um líder
2. Qualquer instrução que seja destino de um desvio é um líder
3. Qualquer instrução que siga imediatamente um desvio é líder
### Grafo de Fluxo
Depois de particionar a RI em blocos básicos, representa-se o fluxo de controle entre eles através de um grafo.
