>## Garbage Collector
>Сборка мусора работает так: когда ссылок на объект больше не существует, то необходимость в нем отпадает, и память, занимаемая им, может быть освобождена. Сборка мусора возникает время от времени во время исполнения программы. 
>Проверить, сколько памяти занимает блок кода, можно следующим способом.
```java
    Runtime r = Runtime.getRuntime();
    System.out.println("1. Total memory is: " + r.totalMemory()/1024/1024 + " MB");
    \\ some code...
    r.gc(); \\ garbage collector call
    System.out.println("2. Initial free memory: " + r.freeMemory()/1024/1024 + " MB");
```
>## Reachability
>[java docs](https://docs.oracle.com/javase/7/docs/api/java/lang/ref/package-summary.html#reachability)
>Разные уровни достижимости характеризуют жизненный цикл объекта:
- strongly reachable
>если объект только что создан
- softly reachable
- weakly reachable
- phantom reachable
- unreachable
> // тут что-то странное, пусть пока что полежит
>**Объект в памяти занимает 16 байт (х64): 12 -- object header, + еще 4 (до деления на 8 без остатка)**.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI4NzM4NTE3MF19
-->