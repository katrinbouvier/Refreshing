>## Hierarchy
>Все ошибки наследуются от интерфейса Throwable.
>Есть Error (Unchecked) и Exception (Checked). Проверяемые исключения появляются там, где отказ предвиден заранее. Непроверяемые исключения сообщают о том, что программа не может выполниться из-за ошибки программиста. RuntimeException является непроверяемым, но наследуется от Exception.

try {
	// block of code to monitor errors
} catch (Exception e) {
	// exception handler
} finally {
	// code 
}
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MDk0MjI4ODYsNjIwNjg3NDAzLC0xMj
U0Mzg2MjU4XX0=
-->