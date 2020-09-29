17/07/20
>## Packages and Interfaces
>**Пакеты** - это контейнеры для классов, они используются, чтобы сохранить пространство имен класса отделенным. 
>
>С помощью ключевого слова **interface** Java позволяет полностью абстрагировать интерфейс от его реализации. Используя интерфейс, можно определять набор методов, который затем реализуется одним или более классами. Интерфейс не содержит реализаций методов. Класс может реализовывать несколько интерфейсов, но не может наследоваться от нескольких абстрактных классов. 
>Интерфейсы указывают классу что делать, но не указывают как. Интерфейсы разработаны, чтобы поддерживать динамическое разрешение методов во время исполнения. Интерфейсы разделяют определение метода (или набора методов) от иерархии наследования классов. 
>[Разница между абстрактными классами и интерфейсами](https://javarush.ru/groups/posts/1985-raznica-mezhdu-abstraktnihmi-klassami-i-interfeysami)
```java
    interface Callback() {
	    void callback(int param);
    }

    class Client implements Callback {
	    // Implement Callback's interface
	    public void callback(int p) {
		    System.out.println("callback called with " + p);
		}
	    
	    void nonIfaceMeth() {
		    System.out.println("nonIfaceMeth() called");
		}
    }
    
    class TestIface {
	    public static void main (String args[]) {
		    Callback c = new Client();
		    c.callback(42);
	    }
	}
```
>Переменная `c` может быть использована, чтобы получить доступ к методу `callback()`, она не может обращаться к другим членам класса Client. Ссылочной переменной интерфейса известны только те методы, которые объявлены в объявлении **интерфейса**. 
```java
    class AnotherClient implements Callback {
    	public void callback(int p) {
    		System.out.println("p squared is " + (p*p));
    		}
    	}
    }
    
    class TestIface2 {
    	public static void main(String args[]) {
    	Callback c = new Client();
    	AnotherClient ac = new AnotherClient();
    	c.callback(42);
    	c = ac; // c now refers to AnotherClient object
    	c.callback(42);
    	}
    }
```
>Версия `callback()`, которая будет вызвана, определяется типом объекта, на который ссылается `c` во время исполнения. 

19/07/20
>## Partial Implementations
>Когда класс реализует интерфейс, но не полностью реализует все требуемые им методы, тогда этот класс должен быть объявлен как **абстрактный**.
>
>Любой класс, наследующийся от `Incomplete`, должен быть объявлен как `abstract` или реализовывать интерфейс `Callback`.
>Абстрактный класс отличается от интерфейса тем, что содержит состояние и поведение. Интерфейс содержит только поведение.
```java
     abstract class Incomplete implements Callback {
        	int a, b;
        	void show() {
        		//...
        	}
        }
```
>## Extending Interfaces
>Abstract class can extend another abstract class. Example:
>`class ArrayList<E>` -**extends**-> `abstract class AbstractList<E>` -**extends**-> `AbstractCollection<E>`
>Interface 
>
			
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2NjM1NjI4LC0yMDE5MTI4Mjc4LDcwNz
I4OTMyLC0xNzg2NDY2MTQ2LDUwNTcxODg2OV19
-->