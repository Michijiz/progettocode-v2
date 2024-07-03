<!-- @format -->

# LE FUNZIONI ASINCRONE

` in JavaScript sono funzioni che eseguono operazioni asincrone e ritornano una Promise. Utilizzando funzioni asincrone, è possibile eseguire operazioni che richiedono tempo (come chiamate API, operazioni di I/O, operazioni di rete) senza bloccare il thread principale dell'applicazione. Questo permette di scrivere codice più reattivo e performante.`

`Per dichiarare una funzione asincrona, si utilizza la parola chiave async`

```js
async function fetchUserData(userId) {
  // Simulazione di una chiamata API asincrona
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const users = {
        1: { name: 'Alice', age: 30 },
        2: { name: 'Bob', age: 25 },
        3: { name: 'Charlie', age: 35 },
      };
      const user = users[userId];
      if (user) {
        resolve(user);
      } else {
        reject('Utente non trovato');
      }
    }, 1000);
  });
}
```

`Nell'esempio sopra, fetchUserData è una funzione asincrona che simula una chiamata API ritardata di un secondo. Restituisce una Promise che si risolve con i dati dell'utente corrispondente all'ID fornito o si rigetta se l'utente non viene trovato.`

## I VANTAGGI DELLE FUNZIONI ASINCRONE

`Le funzioni asincrone, insieme ad async e await, offrono diversi vantaggi:`

`Leggibilità: Il codice risulta più chiaro e leggibile, evitando callback annidati ("callback hell").`

`Gestione degli errori: È più semplice gestire gli errori utilizzando try/catch.`

`Performance: Le operazioni asincrone consentono all'applicazione di rimanere reattiva, evitando il blocco del thread principale`

# PROMISE

`Una Promise in JavaScript è un oggetto che rappresenta il risultato di un'operazione asincrona. Le Promises sono utilizzate per gestire le operazioni asincrone in modo più leggibile e gestibile rispetto ai callback annidati ("callback hell"). Una Promise può essere in uno di questi stati:`

`Pending: Stato iniziale, quando la Promise è in attesa che l'operazione asincrona venga completata.`

`Fulfilled (Risolto): Quando l'operazione asincrona è stata completata con successo.`

`Rejected (Respinto): Quando l'operazione asincrona non è stata completata con successo, ha generato un errore o è stata rifiutata.`

`Le Promises consentono di concatenare operazioni asincrone in modo sequenziale utilizzando i metodi .then() e .catch(), rendendo il codice più leggibile e gestibile rispetto ai callback annidati`

ESEMPIO DI UTILIZZIO DELLE PROMISES

```js
function asyncOperation() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true;
      if (success) {
        resolve('Operazione completata con successo');
      } else {
        reject('Operazione fallita');
      }
    }, 2000);
  });
}

asyncOperation()
  .then(result => {
    console.log(result); // Output: Operazione completata con successo
  })
  .catch(error => {
    console.error(error); // Output: Operazione fallita
  });
```

# CALLBACK HELL

`Callback hell, o "infernale annidamento di callback", si verifica quando si hanno molti callback annidati all'interno di altri callback. Questo scenario si presenta spesso quando si gestiscono operazioni asincrone in JavaScript utilizzando solo i callback, rendendo il codice difficile da leggere, mantenere e debuggare.`

esempio di callback hell:

```js
asyncOperation1(result1 => {
  asyncOperation2(result1, result2 => {
    asyncOperation3(result2, result3 => {
      // E così via...
    });
  });
});
```

## TRY/CATCH CON ASYNC/AWAIT

`Try/catch è un costrutto utilizzato in molti linguaggi di programmazione, inclusi JavaScript e TypeScript, per gestire gli errori in modo controllato. Il blocco try contiene il codice che potrebbe generare un errore, mentre il blocco catch viene utilizzato per gestire e recuperarsi dall'errore se si verifica durante l'esecuzione del blocco try.`

`Async/Await è un'aggiunta sintattica di JavaScript introdotta con ECMAScript 2017 che semplifica la gestione delle Promises e rende il codice asincrono più simile alla programmazione sincrona. Le parole chiave async e await consentono di scrivere il codice asincrono in un modo che sembra sincrono, migliorando la leggibilità e la manutenibilità del codice.`

_esempio di utilizzio di try/catch con async/await_

```js
async function asyncOperation() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true;
      if (success) {
        resolve('Operazione completata con successo');
      } else {
        reject('Operazione fallita');
      }
    }, 2000);
  });
}

async function example() {
  try {
    const result = await asyncOperation();
    console.log(result); // Output: Operazione completata con successo
  } catch (error) {
    console.error('Si è verificato un errore:', error); // Output: Operazione fallita
  }
}

example();
```

`In questo esempio, la funzione asyncOperation restituisce una Promise che si risolve dopo 2 secondi. La funzione example è dichiarata come async e utilizza await per aspettare il completamento di asyncOperation, gestendo eventuali errori nel blocco catch.`
