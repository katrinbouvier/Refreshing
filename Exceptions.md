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

>*Следует помнить о [NaN](https://www.baeldung.com/java-not-a-number) при обработке ошибок. Некоторые операции с неопределенным результатом вместо выброса исключения могут вернуть NaN, -Infinity или Infinity. NaN != NaN is true.*

>Блок catch нужно написать так, чтобы после выбрасывания ошибки программа продолжала работу в нормальном режиме.
>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDEwNDQ1NjIsMTM5NTk3OTI5MSwxOD
k4OTgxNTQ3LDYyMDY4NzQwMywtMTI1NDM4NjI1OF19
-->