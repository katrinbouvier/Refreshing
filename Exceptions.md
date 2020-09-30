>## Exception Handling
>Все ошибки наследуются от класса Throwable.
>Есть Error (Unchecked) и Exception (Checked). Проверяемые исключения появляются там, где отказ предвиден заранее. Непроверяемые исключения сообщают о том, что программа не может выполниться из-за ошибки программиста. RuntimeException является непроверяемым, но наследуется от Exception. Кастомные классы ошибок тоже наследуются от Exception.
```java
try {
	// block of code to monitor errors
} catch (Exception e) {
	// exception handler
} finally {
	// code to be executed after try block ends
}
```
>Выражение **try-with-resources** используется, например, при работе с потоками. Поток автоматически закрывается, когда выполняется блок try.

>*Следует помнить о [NaN](https://www.baeldung.com/java-not-a-number) при обработке ошибок. Некоторые операции вместо выброса исключения могут вернуть NaN, -Infinity или Infinity.*
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzg3MDU3ODA0LDE4OTg5ODE1NDcsNjIwNj
g3NDAzLC0xMjU0Mzg2MjU4XX0=
-->