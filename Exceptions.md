>## Exception Handling
>Все ошибки наследуются от класса Throwable.
>Есть Error (Unchecked) и Exception (Checked). Проверяемые исключения появляются там, где отказ предвиден заранее. Непроверяемые исключения сообщают о том, что программа не может выполниться из-за ошибки программиста. RuntimeException является непроверяемым, но наследуется от Exception.
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NjcxNTM4NTMsNjIwNjg3NDAzLC0xMj
U0Mzg2MjU4XX0=
-->