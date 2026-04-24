### Overview de aprendizagem supervisionada
Um modelo de aprendizagem supervisionada, faz parte de uma família de equações e mapeia uma ou mais entradas à uma ou mais saídas.
Inclui parâmetros que afetam a saída da equação.
Notação:
Input: 
$$x$$
Output: 
$$y$$
modelo 
$$y = f[x]$$
Parâmetros:
$$\phi$$
Modelo:
$$y = f[x, \phi]$$
A função de perda (loss function) mede o quão ruim um modelo é:
$$L[\phi, f[x, \phi], \{x_i,y_i\}^I_{i=1}]$$
Treinar é a descoberta dos parâmetros que minimizam a função de perda
$$\phi = argmin[L[\phi]]$$
