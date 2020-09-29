29/07/20
>## Generics
>Термин *generics* значит *parameterized types* (параметризованные типы). Параметризованные типы позволяют создавать классы, интерфейсы и методы, в которых типы данных, которые они обрабатывают, указываются в качестве параметра. Класс, интерфейс или метод, который работает с параметризованными типами, называется *обобщенным классом* или *обобщенным методом*.
```java
	// T - это параметр типа, который будет заменен реальным типом
	// при создании объекта типа Gen
    class Gen<T> {
    	T ob;
    	
    	Gen(T o) {
    		ob = o;
    	}
    	
    	T getob() {
    		return ob;
    	}
    	
    	void showType() {
    		System.out.println("Type of T is " + ob.getClass().getName());
    	}
    }
    class GenDemo {
	    public static void main(String [] args) {
		    Gen<Integer> iOb;
		    iOb = new Gen<Integer>(80);
		    iOb.showType();
		    int v = iOb.getob();
		    System.out.println("value: " + v);
		    
		    Gen<String> strOb = new Gen<String>("Generics Test");
		    strOb.showType();
			String str = strOb.getob();
		    System.out.println("value: " + str);
		}
	}
```
> Дженерики работают только с ссылочными типами. Нельзя использовать примитивные типы, такие как `int` или `char`. 
>Важно понимать, что ссылка на одну конкретную версию обобщенного типа несовместима с другой версией того же самого обобщенного типа. 
```java
    iOb = strOb; // wrong!
```
    
>## Type Safety of Generics
```java
	// NonGen - функциональный эквивалент
	// класса Gen без обобщений
    class NonGen {
    	Object ob;
    	
    	NonGen(Object o) {
    		ob = o;
    	}
    	
    	Object getob() {
    		return ob;
    	}
    	
    	void showType() {
    		System.out.println("Type of ob is "+ob.getClass().getName());
    	}
    }
```
>Супер-класс `Object` может реализовывать такую же функциональность, как и дженерики, однако его использование не является типо-безопасным по двум причинам.
>Во-первых, для извлечения сохраненных данных требуется явное приведение типов:
```java
    int v = (Integer) iOb.getOb();
```
>Метод `getOb()` вернет тип `Object`, поэтому его нужно привести к типу `Integer`, чтобы выполнить автораспаковку и сохранить значение в переменной. Без явного приведения типов программа не скомпилируется, однако такое приведение может послужить потенциальным источником ошибок.
```java
    iOb = strOb;
    v = (Integer) iOb.getOb();
```
>Здесь переменные `iOb` и `strOb` ссылаются на объекты разных типов. Присваивание синтаксически верно, так как все ссылки `NonGen` одинаковы и любая `NonGen` ссылка может указвать на любой `NonGen` объект. Однако приведение к типу `Integer`, а затем присваивание к `v` во второй строчке вызовет ошибку во время исполнения.
>## A Generic class with Two Type Parameters
```java
    class TwoGen<T, V> {
    	T ob1;
    	V ob2;
    	TwoGen(T o1, V o2) {
    		ob1 = o1;
    		ob2 = o2;
    	}
    }
    //...
    TwoGen<Integer, String> tgObj = new TwoGen<Integer, String>(88, "Generics");
```
>## Bounded Types
>Если необходимо, можно ограничить типы параметров, которые передаются дженерику.
>`<T extends superclass>`
```java
    class Stats <T extends Number> {
    	T[] nums;
    	
    	Stats(T[] o) {
    		nums = o;
    	}
```
>## Wildcard Arguments
>Метасимвльный аргумент типа `Stats<?>` совпадает с любым объектом класса Stats. **?** представляет неизвестный тип.
```java
    boolean sameAvg(Stats<?> ob) {
    	//...
    }
```
>Можно ограничить метасимволы подстановки, например:
```java
    static void showXYZ(Coords<? extends ThreeD> c) {
    	//...
    }
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNzE0OTk0MTgsLTEzMDI5MTQxMjZdfQ
==
-->