>## REST
>[Habr 2017 Mail.ru Group](https://habr.com/en/company/mailru/blog/345184/#comments)
- клиент-серверная архитектура
- REST предоставляет единый интерфейс для взаимодействия компонентов
- сервер не хранит состояние клиента
- многоуровневая система
>## URL
>Сопоставление запросов и URL:
>
|HTTP|URL|explain|button
|--|--|--|--|
|GET|*/posts*|все записи|--|
|POST|*/posts*|создать новую запись|"Save post"|
|GET|*/posts/new*|получить страницу для создания|"Create new post"|
|GET|*/posts/:id/edit*|получить страницу для редактирования|"Edit post"|
|GET|*/posts/:id*|получить одну запись|--|
|PATCH|*/posts/:id*|обновление записи|"Save edited"?|
|DELETE|*/posts/:id*|удаление записи|"Delete post"|
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcxNDc5OTg0OSwtNzk3MzE1NzM0XX0=
-->