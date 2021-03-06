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
>Определяет поведение очереди с двумя концами. Такие очереди могут вести себя как FIFO, и как LIFO. Это обобщеннный интерфейс, расширяет Queue. В Deque есть методы push() и pop(), которые позволяют очереди вести себя как стек.
>## Collection Classes
 - ArrayList Class
> extends AbstractList and implements the List interface. Supports dynamic arrays. ArrayList is variable-length array of object references.
 - LinkedList Class
> extends AbstractSequentialList and implements the List, Deque and Queue interfaces. Linked-list data structure.
 - HashSet Class 
> extends AbstractSet and implements Set interface. Created  a collection, that uses a hash table for storage. Хэшинг -- информационный контент ключа используется, чтобы определить уникальное значение, которое называется хэш код. Хэш код затем используется, как индекс, с котором ассоциированы данные, относящиеся к ключу. Хэширование происходит автоматически. HashSet не гарантирует последовательность элементов, так как процесс хэшинга обычно не сопровождается созданием отсортированного набора. (как положили, можем и не получить) Чтобы сохранить последовательность лучше использовать TreeSet.
 - LinkedHashSet Class
> extends HashSet. Сохраняет связный список в том порядке, в котором элементы положили.
 - The TreeSet Class
> extends AbstractSet and implements NavigableSet interface. Создает коллекцию, которая использует для хранения дерево. Объекты хранятся в отсортированном по возрастанию порядке. Довольно быстрый поиск и получение элементов.
 - PriorityQueue Class
> extends AbstractQueue and implements the Queue interface. Создает очередь, которая имеет приоритет, основанный на компараторе очереди. Изначально вместимость очереди - 11. Если не определен компаратор, используется дефолтный, который сортирует в порядке возрастания. **Осторожно: можно проходить по очереди, используя итератор, но порядок этой итерации не определен. Лучше использовать методы offer() и poll().**
 - The ArrayDeque Class
> extends AbstractCollection and implements the Deque interface. Создает динамический массив и не имеет ограничесний по вместимости. 
 - The EnumSet Class
> extends AbstractSet and implements Set. Специально для использования с элементами типа enum.
>## The Map Interface
>Сопоставляет уникальные ключи со значениями. Ключ -- это объект, по которому в дальнейшем можно получить значение. Мапы -- часть Collection Framework, но они не являются коллекциями. С помощью метода entrySet() можно получить мап как коллекцию. 
 - The SortedMap Interface
>Обеспечивает порядок записей по возрастанию, основываясь на ключах. 
 - The NavigableMap Interface
>Мап, поддерживающий получение записей по самому близкому совпадению с ключом.
 - The HashMap Class
>Использует хэш таблицы для хранения записей. Не гарантирует порядок записей. Дефолтный размер -- 16. 
- The TreeMap Class
> Хранит записи в виде дерева. Гарантирует порядок элементов по возрастанию.
- The LinkedHashMap Class
> Сохраняет порядок элементов, хранит данные в связном списке.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU3OTgwNTMyLDExMjYxNDUzNjUsMTcwMT
A0MjkyLDExMzc0NDk2MCwtMTc3NTM5MDA2NCwtMjUzMDgyMDA3
LC0xMzE3OTcxNzY0LC0xMDIyMjE4NjUwXX0=
-->