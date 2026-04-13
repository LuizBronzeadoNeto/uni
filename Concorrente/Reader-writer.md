O problema de leitor escritor se refere a um conjunto de threads em que um subconjunto precisa realizar uma operação de leitura e outro precisa realizar uma operação de write:
```
Data data = new Data();
Reader
read_data(data); --> região crítica
Writer
write_data(data); --> região crítica 
```
Devido a esse segundo subconjunto a operação de leitura também fica sujeita a condição de corrida. Desse modo, a Solução mais simples envlove a aplicação de um semáforo mutex:
```
mutex = new Semaphore(1);
Reader {
  mutex.wait();
  read_data(data);
  mutex.signal();
}
Writer {
  mutex.wait();   
  write_data(); 
  mutex.signal();
}
```
Essa solução funciona, porém ela deixa a execução desse código um fenômeno puramente serial. Uma maneira de solucionar o problema preservando as vantagens de concorrência, seria uma solução inspirada na catraca da barreira, ou seja, agindo como [[2-thread-locks]]:
```
catraca = new Semaphore(1);
vazio = new Semaphore(1);
readers = 0;
w = new Semaphore(1);

Reader {
  catraca.wait();
  catraca.signal();
  mutex.wait();
  readers++;
  if (readers == 1)
    w.wait();
  r = read_data(data);
  readers--;
  if (readers == 0)
    w.signal();
  mutex.signal();
}

Writer {
  catraca.wait();
  w.wait();
  write_data(data);
  w.signal();
  catraca.signal();
}
```
Assim, a catraca faz com que após a execução de um escritor, uma nova thread será desbloqueada (como em uma catraca real), resolvendo além do problema de race condition, também a questão de starvation, pois o semáforo não diferencia threads reader de threads writer.
Esse padrão também tem relação com o padrão light switch (primeiro a chegar bloqueia e a última a sair libera).
Na prova se Confunde muito read-write lock na construção - PRECISA TER LEITORES E ESCRITORES CONCORRENTES - também há confusão com multiplex e barreira

```

rev 
count = 0
mutex = s(1)
catraca = s(0)
catraca_reutilizavel = s(1)

mutex.wait
count++;
mutex.signal
signal(count == n):
  catraca_reutilizavel.wait()
  catraca.signal()
catraca.wait()
catraca.signal()

mutex.wait()
count--
if count == 0:
  catraca.wait()
  catraca_reutilizavel.signal()
catraca_reutilizavel.wait()
```