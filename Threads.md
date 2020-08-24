23/07/20
>## Threads
>У потока существует несколько состояний:
> - running (запущен и работает)
> - ready to run (запустится, как получит CPU)
> - suspended (временно приостановлен)
> - resumed (возобновен)
> - blocked (заблокирован, пока ожидает ресурс)
> - terminated (прерван, то есть завершен и не может быть возобновлен)
>
> Java назначает каждому потоку приоритет, который показывает, как его следует обрабатывать относительно других потоков. Приоритет потоков - это числа, которые означают приоритет одного потока относительно другого. Приоритет используется, чтобы определить, когда с одного потока переключиться на другой. Это называется *context switch* (переключение контекста). 
>## Synchronization
>В Java для того, чтобы обеспечить синхронизацию между потоками, используют *monitor*. Как только поток входит в монитор, все другие потоки должны ждать, пока тот не покинет монитор. Например, монитор можно использовать, чтобы защищать общие ресурсы от изменения их более чем одним потоком одновременно. 
>В Java нет класса "Monitor", вместо этого каждый объект имеет свой монитор, который начинает работу, когда для объекта вызван один из методов синхронизации. 
>## The Thread Class & the Runnable Interface
>Thread инкапсулирует поток исполнения. Чтобы создать новый поток, следует либо расширить класс Thread, либо реализовать интерфейс Runnable.
>Некоторые методы класса Thread:
> - getName
> - getPriority
> - isAlive
> - join
> - run
> - sleep
> - start
> 
>## The Main Thread
>Когда программа запускается, один поток немедленно начинает выполняться - главный поток исполнения. Есть 2 важные особенности:
> 1. Это тот поток, от которого затем порождаются все дочерние потоки;
> 2. Обычно этот поток завершается последним, так как он выполняет различные завершающие действия.
>
>Хотя главный поток создается автоматически, его можно контролировать с помощью объекта Thread:

    public static void main(String [] args) {
	    Thread t = Thread.currentThread();
	    t.setName("MyThread");
    
	    try {
		    for (int n = 5; n > 0; n--) {
			    Thread.sleep(1000);
			 }
		} catch (InterruptedException e) {
		  System.out.println("Main Thread Interrupted");
		  }
	}
>## Creating a Thread by implementing `Runnable`

    class NewThread implements Runnable {
    	Thread t;
    	
    	NewThread() {
	    	t = new Thread(this, "Demo Thread");
    	}

	    public void run() {
			try {
				for(int i = 5; i > 0; i--) {
					Thread.sleep(500);
				}
			} catch (InterruptedException e) {
			  System.out.println("Child Interrupted");
			}
		}
	}
	
	class ThreadDemo {
		public static void main(String [] args) {
			NewThread nt = NewThread();
			
			nt.t.start();
	    
		    try {
			    for (int n = 5; n > 0; n--) {
				    Thread.sleep(1000);
				 }
			} catch (InterruptedException e) {
			  System.out.println("Main Thread Interrupted");
			  }
		}
	}
	
>## Creating a Thread by extending `Thread`

    class NewThread extends Thread {
    	NewThread() {
    		super("Demo Thread");
    	}
    	public  void run() {
    		try {
    			for (int i = 5; i > 0; i--) {
    			Thread.sleep(500); }
    		} catch (InterruptedException е) {
    		System.out.println("Child Interrupted");
    		}
    	}
    }
    
    class ExtendThread {
    	public static void main(String [] args) {
    		NewThread nt = new NewThread();
    		
    		nt.start();
    		
    		try {
    			for(int i = 5; i > 0; i--) {
    			Thread.sleep(1000);
    		} catch (InterruptedException е) {
    		System.out.println("Main Thread Interrupted");
    		}
    	}
    }
    
> В классе `Thread` определены несколько методов, которые могут быть перегружены наследующим классом. Среди них обязательно перегружать только метод `run()`. Если вы не хотите перегужать другие методы класса `Thread`, то лучше использовать интерфейс `Runnable`. Также, реаализуя `Runnable`, не нужно наследоваться от класса `Thread`, следовательно, можно наследоваться от какого-либо другого класса. 
>Fork/Join Framework in Java 7: [https://habr.com/ru/post/128985/](https://habr.com/ru/post/128985/)
>## `isAlive()` & `join()`
>Есть 2 способа определить, завершился ли поток. Первый - вызвать `isAlive()` для потока исполнения. Этот метод определен в классе `Thread` и возвращает значение типа `boolean`. Более используемый подход - метод `join()`. Этот метод ожидает, пока поток, для которого он вызван, не завершится. 
>## Using a Factory Method
>Фабричный метод - это метод, который возвращает объект класса. Такие методы используются, когда нужно: задать объекту начальное состояние перед использованием или повторно использовать объект. Фабричный метод создаст поток исполнения, вызовет метод start() для него, а затем вернет ссылку на созданный поток. 
>

	    //a factory method that creates and starts a thread
       public static NewThread createAndStart() {
        	NewThread myThrd = new NewThread();
        	myThrd.t.start();
        	return myThrd;
        }
        
       NewThread nt = NewThread.createAndStart();

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4NjMxMzIwOF19
-->