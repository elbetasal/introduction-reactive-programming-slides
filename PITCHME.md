### Introducción a Programación Reactiva

por Esau Betancourt / [@elbetasal](https://twitter.com/elbetasal)

---
### ¿Quiénes somos?

<img src="assets/images/team.jpg" height="450px" >

+++
### Nearsoft Academy 

![Learning](https://media1.tenor.com/images/5b04f7e51bd8659b985b8aa4f86ffedc/tenor.gif?itemid=4472291)

+++ 
### 3 Fases

- Test de lógica. |
- Entrevista en inglés. |
- Screen. |

---

###  

Agregar foto cool para mostrar como funcionaba antes la web

+++

Agregar otra foto mostrando como es programar actualmente

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

+++

![image](http://tutorials.jenkov.com/images/software-architecture/software-architecture-introduction-3.png)

###### Credit: [Jenkov.com](http://tutorials.jenkov.com/images/software-architecture/software-architecture-introduction-3.png)

---
###Reactive Manifiesto
![reactive](assets/images/reactive-traits-es.svg)
---
Futures and callbacks

---
Observer Pattern

---
RxJava

---
Vert.x

---
Spring
