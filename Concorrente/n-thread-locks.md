### Algoritmo de Bakery
A ideia do algoritmo de bakery é similiar a um consultorio, em que cada thread retira um "ticket" e espera a sua vez, e apenas uma é atendida por vez, garantindo exclusão mútua, enquanto generalizando o algoritmo [[2-thread-locks]].
Cada thread olha o próprio ticket e o ticket de todas as outras threads, e checa para ver se ela tem o menor número no ticket, caso tiver, a thread saberá que é a sua vez:

```c
int tickets[n];
count = 0;
void lock()
{
	//sorteio
	int max = 0;
	for(int ticket : tickets) 
	{
		if (ticket > max) max = ticket;
	}
	tickets[myId()] = max++; //É uma condição de corrida, o desempate é por id
	
	//actual lock code
	for (int i = 0; i < n; i++)
	{
		while(!tickets[i] == 0 && tickets[i] < tickets[my_id] || 
		(tickets[i] == tickets[my_id] && i < my_id));
		
	}
	
}

```

Para realizar unlock no algoritmo de bakery, basta resetar o número do ticket no id da thread de volta para o nulo (neste caso 0), desta forma o indice ficará pronto para reuso da próxima vez que a thread quiser entrar:

```c
void unlock()
{
	tickets[my_id] = 0;
}
```
