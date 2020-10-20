>## Logging
```java
private static final Logger log = LoggerFactory.getLogger(Application.class);
log.info("Some info");
```
>## Computation time
```java
long m1 = System.currentTimeMillis();  
//some code
System.out.println((double)(System.currentTimeMillis() - m1)/1000 + " sec");
```
>## Naming
>Если сущность *Person*, то контроллер следует назвать *PeopleController*.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwODA3ODY3NzcsMTg4ODIyNTk2LC01MT
E3NzI0MDMsLTE2NjA3MTg4MDRdfQ==
-->