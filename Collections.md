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
>Определяет поведение очередт с двумя концами. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTc4MDg1NzQxLC0yNTMwODIwMDcsLTEzMT
c5NzE3NjQsLTEwMjIyMTg2NTBdfQ==
-->