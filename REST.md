>## REST
>[Habr 2017 Mail.ru Group](https://habr.com/en/company/mailru/blog/345184/#comments)
- клиент-серверная архитектура
- REST предоставляет единый интерфейс для взаимодействия компонентов
- сервер не хранит состояние клиента
- многоуровневая система
>## URL
>Сопоставление запросов и URL:
>
|HTTP|URL|explain|кнопка
|--|--|--|--|
|GET|/posts|все записи|-|
|POST|/posts|создать новую запись|"Save post"|
|GET|/posts/new|получить страницу для создания|""|
|GET|/posts/:id/edit|получить страницу для редактирования||
|GET|/posts/:id|получить одну запись||
|PATCH|/posts/:id|обновление записи||
|DELETE|/posts/:id|удаление записи||
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkwMjA0MzkxMiwtNzk3MzE1NzM0XX0=
-->