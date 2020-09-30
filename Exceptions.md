>## Hierarchy
>Все ошибки наследуются от интерфейса Throwable.
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
>try-with-
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAxNjE1NDQ0NCw2MjA2ODc0MDMsLTEyNT
QzODYyNThdfQ==
-->