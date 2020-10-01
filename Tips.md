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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4ODIyNTk2LC01MTE3NzI0MDMsLTE2Nj
A3MTg4MDRdfQ==
-->