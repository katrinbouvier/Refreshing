30/07/20
>## Overview
>Collections Framework является высокоэффективным, также разные типы коллекций работают похожим образом. 
>## Colllections Hierarchy
>[Number 4 is schema of Collections hierarchy](https://javastudy.ru/interview/collections/)
>Map -- это отдельный интерфейс, в Collection не входит.  Иерархия `TreeMap<K, V>` схожа с `TreeSet<E>`.
>## The Queue Interface
>Обобщенный интерфейс, расширяет базовый интерфейс Collection и определяет поведение очереди. В Queue определены методы:
> - E element()
> - boolean offer(E obj)
> - E peak()
> - E poll()
> - E remove()
>Элементы в очередь добавляются в голову. Разница между poll() и remove() в том, что poll() вернет null, если очередь пустая, а remove() выбросит исключение.
>## The Deque Interface
>Определяет поведение очередь с двумя концами. Такие очереди могут вести себя как FIFO, и как LIFO. Это обобщеннный интерфейс, расширяет Queue. В Deque есть методы push() и pop(), которые позволяют очереди вести себя как стек.
>## Collection Classes
> - ArrayList Class
> extends AbstractList and implements the List interface. Supports dynamic arrays. ArrayList is variable-length array of object references.
> - LinkedList Class
> extends AbstractSequentialList and implements the List, Deque and Queue interfaces. Linked-list data structure.
> - HashSet Class 
> extends AbstractSet and implements Set interface. Created  a collection, that uses a hash table for storage. Хэшинг -- информационный контент клю
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkzNTgzODg5OSwxNzAxMDQyOTIsMTEzNz
Q0OTYwLC0xNzc1MzkwMDY0LC0yNTMwODIwMDcsLTEzMTc5NzE3
NjQsLTEwMjIyMTg2NTBdfQ==
-->