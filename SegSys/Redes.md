### Segurança em redes
* Firewall: ponto central que concentra entrada e saída
Um firewall ideal teria o mesmo contexto que o usuário para averiguar cada mensagem individualmente.
#### Configuração de firewalls
Pode existir uma maquina "bastião", fortalecida (hardened) sem serviços desnecessários, que pode executar proxies.
Pode também ser um componente de software (embora com maior risco) ou um dispositivo de rede.
Podem ser várias redes, em cascata ou até estrela.
* DMZ (ex: usando roteadores NAT domésticos para colocar dispositivos não confiáveis separados)
Segmentação é uma estratégia comum.
#### Sistemas de detecção de intrusão
IDS (intrusion detection system), IPS (intrusion prevention system), IDPS (intrusion detection and prevention system).
Alguns são baseados em assinaturas, detectando padrões de acesso na maquina e na rede, enquanto outros são baseados em anomalias, assumindo que um modelo da normalidade pode ser derivado.

#### IDS, IPS
Detectar rapidamente, gerenciando erros para não dessensibilizar os operadores ou deixar ataques passarem despercebidos.
Baseado em host, rede ou híbrido.
Esses sistemas devem executar continuamente sem supervisão, tendo uma sobrecarga aceitável e uma política de segurança confiável.
### Arquitetura de confiança zero
#### Redes de confiança zero
Nos modelos convencionais de rede e nuvem, o controle era simples. Nos modelos mais recentes, as implantações são distribuídas e dinâmicas, com múltiplos ambientes, serviços externos. Ou seja, não é possível ter uma segurança de perímetro forte, assumindo-se comprometimento
#### Fundamentos zero-trust
* Identidade
* Autorização
* Monitoramento
