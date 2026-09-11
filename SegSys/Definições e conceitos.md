### Ameaça
É o potencial de dano, existem várias classificações
Exemplos de tipos do livro:
* Divulgação não autorizada
* Fraude
* Interrupção de serviço
* Usurpação
Entender ameaças nos ajuda a entender o que poderia ser feito para evitar que se concretizassem.
Outras classificações:
* CID: Confidencialidade, Integridade, Disponibilidade
* STRIDE: Spoofing, Tampering, Repudiation, Information Disclosure, Elevation of privilege
### Vulnerabilidade
É um Ponto explorável.
Um problema no projeto ou fonte de um software que se não explorada por um agente malicioso, não causaria um estado indesejado. Quando se pensa em vulnerabilidade, se pensa em CVE (Common Vulnerability and Exposures) mantido pelo MITRE, no padrão CVE-[ano]-[seq].
* Padrão da indústria para registro para registro de vulnerabilidades hardware e software
* NVD (National Vulnerability Database) enriquece os CVEs com mais informações
	* Common weakness enumeration (CWE)
	* Common Platform enumeration (CPE)
	* Common vulnerability Scoring system (CVSS)
#### CVSS
* Vetor de ataque:
	* Internet, rede adjacente, acesso direto etc
 * Complexidade (alta, baixa)
 * Requisitos (altos ou baixos)
 * Privilégios (nenhum, usuário, admin)
 * Interação 
 * Impacto em CID no sistema vulnerável e vizinhos
 A versão mais recente é o CVSS 4.0, sendo mais intuitivo e flexível (contém mais métricas), que resulta em mais informações sobre ambiente para refinamento do score. Considera também métricas suplementares (como automatização).
### Ataque 
É a exploração da vulnerabilidade
#### Superfice de ataque
A superfíce de ataque compreende todos os pontos onde um atacante pode tentar ou extrair dados de um ambiente.
Tipos:
* Rede
* Software
* Pessoas
#### Atacantes
"There are two types of encryption: one will prevent your sister from reading your diary and one that will prevent your government."

Podem ser indivíduos ou organizações que realizam ataques benignos ou maliciosos. Pode originar internamente numa organização ou externamente.
Um atacante pode se reunir a um vândalo que almeja apenas o dano ou um cibercriminoso, que busca algum ganho. 
Podem ser direcionados (APT) ou aleatórios (ransomware).

### Compromentimento
A concretização da ameaça
Ciclo Ameaça -> Vulnerabilidade -> Ataque -> Comprometimento pode ser quebrada em diversos pontos
Tipos de mecanismos:
* Prevenção
* Obstáculos
* Reflexão
* Mitigação
* Recuperação

