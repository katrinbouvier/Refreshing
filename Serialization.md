>## Serialization
>Это процесс записи состояния объекта (данные, которые он хранит) в поток байтов. Полезно, когда надо сохранить объект в постоянное хранилище, такое как файл. *RMI (Remote Method Invocation).* Java также безопасно обрабатывает объекты со сложной структурой. Если объект хранит ссылки на другие объекты, то они тоже сериализуются. Граф отношений объектов. 
>Пример:
```java
class Engine implements Serializable {  
	private String model;  
	private int power;
	 
	Engine(String model, int power) {  
		this.model = model;  
		this.power = power;  
	}  
	
// getters & setters

}  
  
class Car implements Serializable {  
	private Engine engine;
	private String brand;
	
	Car(){}

	Car(Engine engine, String brand) {  
		this.engine = engine;  
		this.brand = brand;  
	}

	// getters & setters

	@Override  
	public String toString() {  
		return "Car brand is " + this.getBrand() + "; " +  
		       "car engine is: " + this.getEngine();  
	}
}  

public class Main {  
	public static void main(String[] args) {  

		Engine engine = new Engine("SuperEngine3000", 1200);  
		Car car  = new Car(engine, "Ferrari");  

		System.out.println(car);  

		// serialization  

		try(ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("serial"))) {  
			oos.writeObject(car);  
		}  
		catch (IOException e) {  
			System.out.println("Some problem arised while serializing: "+ e);  
		}  

		// deserialization  

		Car newCar = new Car(); 
		 
		// very nicely closes stream for you
		try(ObjectInputStream oos = new ObjectInputStream(new FileInputStream("serial"))) {
			// 
			newCar = (Car)oos.readObject();  
		}  
		catch (ClassNotFoundException | IOException e) {  
			System.out.println("Some problem arised while deserializing: "+ e);  
		}  
		System.out.println(newCar);
	}  
}
```
>Классы, ссылки на которые есть в сериализуемом классе, должны реализовывать интерфейс Serializable или наследовать класс, который реализует этот интерфейс. Иначе -- *java.io.NotSerializableException*
>Если пометить поле как **transient**, то оно не будет сериализовано. 
transient private String brand;

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjg1NDYxMDcyLC0xNTYxNTQxNTU5XX0=
-->