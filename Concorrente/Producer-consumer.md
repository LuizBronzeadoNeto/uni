Existência de um Producer e um consumer em um buffer compartilhado
```java
Buffer b = new buffer();
mutex = new Semaphore(1);
bufferS = new Semaphore(BUFFER_SIZE);
Producer:
data = produce();        
bufferS.wait()
mutex.wait();
b.add(data);		
mutex.signal();

Consumer
mutex.wait()
data = b.get();
mutex.signal();
consume(data);
bufferS.signal();
```
Porém surgem problemas em um ambiente com n consumidores e n produtores no buffer.
Uma solução possível é a criação de um mutex que protege as regiões críticas, porém isso tornaria a solução em algo completamente serial. É preciso também sinalizar o consumidor quando algo for adicionado ao buffer (caso contrário ele tentaria processar um buffer vazio):
```java
dataSignal = new Semaphore(0);
	consumer{
		mutex.wait();
		dataSignal.wait();
		...}
	Producer{
		...
		dataSignal.signal();}
```
Vale salientar que dentro de mutex, não se deve ter nenhum semáforo, pois arrisca deadlock.

```java
Linked List
mutex = new Semaphore(1);
head = null;

insert(data)
{
    node = new(data);
    mutex.wait();
    node.next = head;
    head = node;
    mutex.signal();
}

remove(data)
{
    mutex.wait();
    if (head == null)
        return
    if (head.data == data)
        head = head.next;
    current = head
    while (current.next != null && current.next.data != data)
    {
        current = current.next;
    }
    if (current.next != null)
        current.next = current.next.next;
    mutex.signal();
}
```