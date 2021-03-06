### Introducción a Programación Reactiva

por Esau Betancourt / [@elbetasal](https://twitter.com/elbetasal)

---
### ¿Quiénes somos?

<img src="assets/images/team.jpg" height="450px" >

+++
### Nearsoft Academy 

![Learning](assets/images/learn.gif)

+++ 
### 3 Fases

- Test de lógica. |
- Entrevista en inglés. |
- Screen. |

---

###  

![web](assets/images/web.png)

+++

<img src="assets/images/Internet_of_Things.jpg" height="450px" >

<label style="font-size: 14px;"> Graphic by Wilgengebroed on Flickr [CC BY 2.0 (http://creativecommons.org/licenses/by/2.0)], via Wikimedia Commons</label>

+++
##### Reactive programming. 
Un modo de desarrollo enfocado en la observacion de streams de datos, reaccionando a cambios y propagándolos.

+++ 

### Streams

![stream](assets/images/stream.png)

+++ 

### ¿Cuándo usarlo?


+++

### Diseñando una API Reactiva

- Usa comunicación asíncrona via eventos 
- Piensa en término de flujos de eventos. | 

+++
### No bloquees
![wait](assets/images/waiting.gif)

+++

![image](assets/images/software-architecture-introduction-3.jpg)

+++
### Imperativa

```java
ResponseEntity<Double> piNumber = 
  restTemplate.exchange("http://localhost:8080/pi", 
    HttpMethod.GET, HttpEntity.EMPTY, Double.class, 
    new HashMap<>());
return "Hello "+ 
          name + 
        " your PI number is :" + 
        piNumber.getBody();
```
+++

### Reactiva
```java
Mono<Double> doubleMono = 
  webClient.get()
           .uri("/pi" , new HashMap<>())
           .retrieve()
           .bodyToMono(Double.class);
return doubleMono
  .map(a -> "Hello " +
            serverRequest.pathVariable("name") + 
            "your PI number is: "+ 
            a)
  .flatMap(helloWithPi -> ServerResponse.ok()
                          .contentType(MediaType.TEXT_PLAIN)
                          .body(BodyInserters
                                .fromObject(helloWithPi)));
```
---

#### Reactive system 
An architecture style used to build responsive and robust distributed systems based on asynchronous message-passing.

+++
### Reactive Manifiesto
![reactive](assets/images/reactive-traits-es.svg)

--- 
### Futuros 

```
get()

get(long timeout, TimeUnit unit)
```

+++

### CompletableFuture

```

supplyAsync(Supplier<U> supplier)

thenAcceptAsync(Consumer<? super T> action)

thenComposeAsync(Function<? super T, ? extends CompletionStage<U>> fn)

thenCombineAsync(CompletionStage<? extends U> other,BiFunction<? super T,? super U,? extends V> fn)

exceptionally(Function<Throwable, ? extends T> fn)


```

---

### RxJava

 Es una librería Java que implementa las ReactiveX (extensiones reactivas ).</br> 
 `Se basa en la composición asíncrona y programas basados en eventos , mediante el uso de secuencias observables.`

+++

 ### ¿Porqué?

- Legibilidad 
- Simplicidad | 
- Lazyness. |
 

+++ 

 ### Clases Base

```
io.reactivex.Flowable: 0..N flows, supporting Reactive-Streams and backpressure 
io.reactivex.Observable: 0..N flows, no backpressure 
io.reactivex.Single: a flow of exactly 1 item or an error
io.reactivex.Completable: a flow without items but only a completion or error signal 
io.reactivex.Maybe: a flow with no items, exactly one item or an error

```
+++  

### Push vs Pull 
Estamos acostumbrados a un modelo donde le pedimos al productor un nuevo elemento cada vez que lo necesitamos (Pull) en vez de que el productor nos avise de cuando está disponible (Pull). En ocasiones provoca bloquear al usuario hasta que esté disponible. 

+++
###  Eventos 

Un elemento observable puede producir 3 tipos de eventos : 
- Evento normal 
- Evento de terminación 
- Evento de error

+++ 
### Reactive Streams

Una initiava para proveer un estándar para el procesamiento asíncrono de stream con back pressure.

+++
### Operadores
http://rxmarbles.com/

---

### Otras opciones

- [VertX](http://vertx.io/)  
- [Spring Reactor](https://projectreactor.io/)
- [Akka Streams](https://doc.akka.io/docs/akka/2.5.5/scala/stream/index.html)
