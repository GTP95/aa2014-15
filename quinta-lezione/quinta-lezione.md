#Ricorsione: modello di valutazione, approfondimento

È possibile scrivere una funzione che richiama se stessa all'infinito o finchè non verrà raggiunto un certo risultato. Questo secondo caso è molto utile perchè permette di effettuare calcoli ricorsivi. Poniamo ad esempio di dover scrivere una funzione che calcoli il fattoriale di un numero, possiamo scriverla così:
 ```
def fattoriale(x):  
 if x>1  
  return x*fattoriale(x-1)  
 else:  
  return 1  
   ```
Analizziamo il codice python sopra riportato. La prima linea di codice definisce la funzione "fattoriale(x)" mentre la seconda introduce un controllo che stabilisce che se "x" è maggiore di 1 allora il suo valore verrà moltiplicato per il risultato della medesima funzione ma calcolato utilizzando un valore di "x" diminuito di un'unità (terza linea) altrimenti la funzione ritorna come valore 1 (penultima e ultima linea). Ciò significa che dato in ingresso un certo valore di "x" esso verrà moltiplicato per tutti i numeri precedenti finchè si raggiunge il valore x=1 (seguendo la definizione ricorsiva di fattoriale: n!=n(n-1)(n-2)...(n-n+1)), a questo punto la funzione termina restituendo il valore così calcolato.
#Valutazioni che non terminano -> problema dell'arresto (introduzione, implicazioni)

Come accennato prima, è possibile scrivere funzioni che non terminano mai. Ecco un semplice esempio:
```
def ricorsioneinfinita():
 return ricorsioneinfinita()
```
Come si può facilmente notare, questa funzione continuerà a richiamare se stessa perchè non è stata definita una condizione di uscita. Ci sono però anche casi in cui una funzione proseguirà all'infinito nonostante sia stata determinata una condizione d'uscita. Ad esempio, ammettendo di disporre di un calcolatore con memoria e potenza di calcolo infinite, una funzione che genera numeri primi non terminerà mai, poichè i numeri primi sono infiniti. Questo porta al problema dell'arresto, deinito da Alan Turing, che consiste nel chiedersi se, data una funzione, è sempre possibile stabilire se terminerà o meno. Turing ha dimostrato che nonostante sia possibile definire matematicamente una funzione che permette di stabilire se un'altra funzione terminerà o meno questa non è valutabile, dunque non è possibile stabilire per tutte le funzioni se termineranno o meno. D'altronde se disponessimo di uno strumento così potente si potrebbero risolvere molti grandi problemi matematici. Per esempio ad oggi non esiste alcuna dimostrazione dell'infinità o meno dei numeri primi gemelli mentre è semplice scrivere una funzione che li cerchi. Se passassimo questa funzione alla funzione che permette di determinare se una funzione termina o meno, avremmo la dimostrazione che i primi gemelli sono o non sono infiniti. 
 
 
 
#ricorsioni `lineari`: controllo di primalità di un numero.

La ricorsione ha molte possibili applicazioni, un altro esempio oltre a quello precedentemente visto di calcolo del fattoriale di un numero può essere una funzione che determina se un numero è primo. Per rendere questo compito più semplice possiamo scomporre il problema in due parti e risolverle separatamente. Partiamo dalla definizione di numero primo: un numero è primo quando è divisibile solo per se stesso e per 1. Possiamo dunque pensare di avere una funzione "h(n,i)" che restituisce il primo divisore di "n" più grande di "i". Se poniamo i=1 e il valore restituito è uguale al numero da controllare, allora quest'ultimo è primo. A questo punto la funzione per controllare se un numero è primo sarà:

```
def primo(x):
 if h(x,1)==x:
  return 1
 else:
  return 0
  ```
 Adesso scriviamo la funzione "h(n,i)":
 
 ```
 def h(n,i):
  if n%(i+1)==0:
   return i+1
  else:
   return h(n,i+1)
```

In questo caso la ricorsione è usata nella funzione "h(n,i)" per continuare ad incrementare la variabile "i" finchè non ottiene un divisore di "n".
