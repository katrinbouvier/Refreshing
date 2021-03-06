>## Exception Handling
>Все ошибки наследуются от класса Throwable.
>Есть Error (Unchecked) и Exception (Checked). Проверяемые исключения появляются там, где отказ предвиден заранее. Непроверяемые исключения сообщают о том, что программа не может выполниться из-за ошибки программиста. RuntimeException является непроверяемым, но наследуется от Exception. Кастомные классы ошибок тоже наследуются от Exception.
```java
try {
	// block of code to monitor errors
} catch (Exception ex) {
	// exception handler
} finally {
	// code to be executed after try block ends
}
```
>Выражение **try(SomeStream ss = new SomeStream(...))** используется, например, при работе с потоками. Поток автоматически закрывается, когда выполняется блок try. *try-with-resources*

>*Notice: следует помнить о [NaN](https://www.baeldung.com/java-not-a-number) при обработке ошибок. Некоторые операции с неопределенным результатом вместо выброса исключения могут вернуть NaN, -Infinity или Infinity. NaN != NaN is true.*

>Блок catch нужно написать так, чтобы после выбрасывания ошибки программа продолжала работу в нормальном режиме.
>Пример try-catch:
```java
try {
	throw new NullPointerException("Some message");
} catch (NullPointerException | AnotherException ex) {
	sout(ex.getMessage()); // will return "Some message"
	//sout(ex); will return "exceptionClass : Some message"
}
```
>Declaring that method throws exception:
```java
public void myMethod() throws IndexOutOfBoundsException {
	//...
	throw new IndexOutOfBoundsException();
}
//...
try {
	myMethod();
} catch (IndexOutOfBoundsException ex) {
	//...
}
```
>finally используется, чтобы после выбрасывания ошибки метод сделал все, что ему требуется (например, после чтения файла -- закрыть его). finally выполняется в любом случае, неважно, была выброшена ошибка или нет.
>Notice: операторы обработки исключений Java не должны рассматриваться как общий механизм нелокального ветвления. [Пример](https://stackoverflow.com/questions/26134896/why-java-s-exception-handling-statements-should-not-be-considered-a-general-mech). Local branching -- когда if-else выполняется в одном месте, например, в методе. Это делает код более понятным. Если ветвление разбросано по нескольким местам, то это может сделать код менее читаемым и уязвимым.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDAyMzIzNywxMjY1MTY0MTc1LC05OT
U5NjE5NzcsMTE4MTYyNDk0OSwtMzc0NDI1Mjc5LC0xOTQxMDQ0
NTYyLDEzOTU5NzkyOTEsMTg5ODk4MTU0Nyw2MjA2ODc0MDMsLT
EyNTQzODYyNThdfQ==
-->