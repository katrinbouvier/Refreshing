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
>Выражение try-with-resources используется, например, при р
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAwMTU5MTY4OSw2MjA2ODc0MDMsLTEyNT
QzODYyNThdfQ==
-->