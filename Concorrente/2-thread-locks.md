Ambas as funções dos semáforos tem uma uma região crítica, locks são feitas para proteger essas regiões críticas, sendo baseadas em instruções de maquinas especiais:
			                TEST-AND-SET
que operam em um ciclo de clock, impossibilitando condições de corrida (um ciclo ' imposibilita trocas de contexto).

```python
boolean flag = false
f():
  while(flag)
  flag = true
  rc()                #bug! não garante exclusão mutua`
  flag = false
  ```
O problema desse código é que você pode ser interrompido entre testar e setar!
Com test-and-set (tst retorna o valor anterior):
```python
f():
  while(tst(flag, t))
  rc()
  flag = false
```
um semáforo usa essa função internamente para garantir exclusão

implementação de lock sem exclusão mutua


```python
flags[boolean] = [false, false]
lock():
  int my_id = get_id()
  while(flags[1 - my_id])
  flags[my_id] = true

unlock():
  int my_id = get_id()
  flags[my_id] = false
```

um algoritmo mais gentil seria quando uma thread chegar, ela deve se barrar, assim quando outra thread chegar, ela escreverá o seu número deixando a primeira entrar na rc
```python
int victim = -1
lock():
  victim = get_id()
  while(victim == get_id());
unlock():
  victim = get_id()
```
Esse algoritmo garante exclusão apenas se tiver mais de uma thread no sistema, se tiver apenas uma, ela ficará travada no while

### BEST OF BOTH WORLDS

```python
flag[boolean] = {false, false}
lock():
  victim = get_id
  other_thread = flags[get_id - 1]
  flags[get_id] = true
  while(flags[get_id - 1] && victim == get_id());
unlock():
  other_thread = false
  victim = get_id()
  ```