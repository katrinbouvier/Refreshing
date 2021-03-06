28/07/20
>## Arrays
>Можно создать массив любого типа, одного или нескольких измерений.
>Чтобы создать массив, требуется 2 шага: объявить переменную желаемого типа; выделить память для массива, используя ключевое слово `new`.

>В Java многомерные массивы представляют собой массивы массивов. 

    int twoD[ ][ ] = new int[4][5];
> Левый индекс обозначает строку, а правый индекс -- столбец. При резервировании памяти под многомерный массив необходимо указать память только для первого измерения массива. Длина каждого массива-элемента из второго измерения может быть разной. 
>## `ArrayList`
>Класс `ArrayList` расширяет `AbstractList` и реализует интерфейс `List`. `ArrayList` -- это обобщенный класс, который декларируется таким образом:

    class ArrayList<E>
>`E` обозначает тип объектов, которые будут храниться в списке. `ArrayList` поддерживает динамические массивы, размер которых можно менять по желанию. По сути, `ArrayList` является массивом переменной длины, который содержит ссылки на объекты. 
>Конструкторы класса ArrayList:

    ArrayList()
    ArrayList(Collection <? extends E> c)
    ArrayList(int capacity)
>Первый конструктор создает пустой список. Второй создает список на основе элементов коллекции `c`. Третий создает список указанной вместимости, по сути, в основе лежит массив, который хранит элементы. Вместимость автоматически увеличивается по мере добавления элементов в список.
>Иногда требуется из списочного массива получить обычный массив, на это есть несколько причин:
> - ускорение выполнения некоторых операций;
> - передача массива в метод, который не перегружается так, чтобы принимать коллекции;
> - чтобы интегрировать код, основанный на коллекциях, в легаси-код, который не понимает коллекции.
> 
> Чтобы получить обычный массив из списочного, используется метод `toArray()`.
>Коллекции могут хранит только ссылки, а не значения примитивных типов. Однако автоматическая упаковка позволяет передать значения типа `int` в метод `add()` без ручного "обертывания" в `Integer`.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTIxMTY3MzE4XX0=
-->