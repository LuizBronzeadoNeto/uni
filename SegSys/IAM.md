### Responsabilização
Uma vez que os usuários são identificados, as operações relevantes devem ser registradas, tipicamente em logs que armazenam quem fez o que e quando.
Dependendo do que se espera do usuário malicioso, os logs podem ser armazenados de diferentes maneiras.
#### Autenticação para não humanos
Assim como para pessoas, quando componentes de software ou dispositivos IoT acessam serviços, eles precisam se autenticar.
Humanos não são facilmente clonados ou reprogramados, mas software sim.

### Identidade e autenticação
Assim como no mundo físico, a identidade deve:
1. ser gerada de forma confiável
2. Estar vinculada a um portador robusto
3. Ser verificada por terceiros

#### Autenticação com crpitografia simétrica
$P \rightarrow Q$ : I am $P$
$Q$ :         generate nonce $n$
$Q\rightarrow P$ : $n$
$P$ :         compute $m' = \{P,Q,n\}_k$
$P \rightarrow Q$ : $m'$
$Q$  :         verify $\{P,Q,n\}_k = m'$
          if equal, accept

#### Ataques comuns
* Força bruta
* Tabelas de hash pré-calculadas (Rainbow Tables)