# Northwind Data Services

![Overview](images/northwind-overview.png)

Обучающая задача по разработке веб-приложений, в которых используется клиент-серверное взаимодействие с внешней информационной системой через внешнее API этой системы для управления внутренними сущностями этой системы. В качестве модели данных используется Northwind.

Используемые технологии:
* ASP.NET
* WCF


## Задача 1 - Northwind OData Service

Цели:

* Изучить модель базы данных Northwind.
* Изучить основы языка запросов OData.
* Научиться использовать язык запросов OData для доступа к данным Northwind OData Service.


### Модель Northwind

В качестве основной модели данных в задаче используется модель учебной базы данных Northwind, схема которой находится в документе [Northwind Sample Database](https://www.zentut.com/wp-content/uploads/downloads/2013/06/Northwind-Sample-Database-Diagram.pdf). Связи между таблицами в диаграмме обозначены с помощью графической нотации "воронья лапка", объяснение которой дано в статье ["Data Modelling using ERD with Crow Foot Notation"](https://www.codeproject.com/Articles/878359/Data-Modelling-using-ERD-with-Crow-Foot-Notation).


#### Выполнение

1. Используя диаграмму, выясните, какие данные хранят в себе сущности модели.
2. Выясните кардинальность для связей между таблицами PK Table (таблица, которая содержит первичный ключ сущности) и FK Table (таблица, содержащая внешний ключ сущности). Заполните колонки Cardinality в таблице:

| PK Table      | Cardinality PK Table | FK Table             | Cardinality FK Table | Relationship |
| ------------- | -------------------- | -------------------- | -------------------- | ------------ |
| shippers      | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| employees     |                      | orders               |                      |              |
| employees     |                      | employees            |                      |              |
| employees     | -                    | territories          | -                    |              |
| customers     |                      | orders               |                      |              |
| customers     | -                    | customerdemographics | -                    |              |
| orders        |                      | orderdetails         |                      |              |
| products      |                      | orderdetails         |                      |              |
| suppliers     |                      | products             |                      |              |
| categories    |                      | products             |                      |              |
| region        |                      | territories          |                      |              |

3. Выясните тип отношений между таблицами базы данных. Заполните колонку Relationship в таблице выше. Используйте статью [Many-to-Many Relationship in the Northwind database](http://blog.codeontime.com/2012/04/many-to-many-relationship-in-northwind.html), если необходимо.


#### Дополнительные материалы

* Гудов, Завозкин, Пфайф. Учебное пособие ["Базы данных"](http://unesco.kemsu.ru/study_work/method/DB/book/index.html)
* Сабитов, Пирогов. Учебный курс ["Введение в СУБД"](https://cmd.inp.nsk.su/~pirogov/DB/slides)


### Northwind OData Service

[OData](https://ru.wikipedia.org/wiki/Open_Data_Protocol) - это открытый стандартизированный протокол для запроса и обновления данных, который позволяет выполнять операции с ресурсами, используя команды ("методы") протокола HTTP.


#### Выполнение

1. Изучите основы протокола HTTP - структуру, основные методы (GET, POST, PUT, DELETE), коды состояния, заголовки. Используйте статьи ["Обзор протокола HTTP"](https://developer.mozilla.org/ru/docs/Web/HTTP/Overview) и ["Простым языком об HTTP"](https://habr.com/ru/post/215117/) в качестве обучающего материала, и [статью в википедии](https://ru.wikipedia.org/wiki/HTTP#%D0%97%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%B8) в качестве справочика.
2. Postman - инструмент для работы с HTTP-сервисами и REST API.
  * Установите [Postman](https://www.getpostman.com/downloads/).
  * Освойте базовые сценарии работы c Postman ([Postman: от простого API-теста до конечного сценария](https://www.youtube.com/watch?v=hGmJMeE_ok0)).
  * Используйте ["Learning OData on Postman"](https://www.odata.org/getting-started/learning-odata-on-postman/), чтобы добавить в Postman коллекцию URL и пройдите ["Basic Tutorial](https://www.odata.org/getting-started/basic-tutorial). 


#### Дополнительные материалы

* OData REST API — мелкие хитрости ([часть 1](https://habr.com/ru/company/databoom/blog/262937/), [часть 2](https://habr.com/ru/company/databoom/blog/263167/), [часть 3](https://habr.com/ru/company/databoom/blog/263435/))


### Northwind Data Model




### Northwind Data Service

В качестве внешнего сервиса будет использоваться [Northwind OData Test Service](https://services.odata.org/V2/Northwind/Northwind.svc/).

Пример использования сервиса через браузер:

1. Перейти на [страницу сервиса](https://services.odata.org/V2/Northwind/Northwind.svc/).

```
https://services.odata.org/V2/Northwind/Northwind.svc/
```

2. Чтобы посмотреть список всех сущностей Customer - добавить "/Customers"

```
https://services.odata.org/V2/Northwind/Northwind.svc/Customers
```

3. Чтобы найти сущность Customer, уникальный идентификатор которого ALFKI.

```
https://services.odata.org/V2/Northwind/Northwind.svc/Customers('ALFKI')
```

4. 

https://services.odata.org/V2/Northwind/Northwind.svc/Customers('ALFKI')/Orders

![Northwind OData Service](images/northwind-odata-service.png)



## Ссылки

### Northwind

http://www.wilsonmar.com/northwind.htm

* [Схема базы данных Northwind](https://www.zentut.com/wp-content/uploads/downloads/2013/06/Northwind-Sample-Database-Diagram.pdf) ()

Схема базы данных Northwind ([в диаграмме использована система обозначений "воронья лапка"](https://www.codeproject.com/Articles/878359/Data-Modelling-using-ERD-with-Crow-Foot-Notation))



* [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)
* [Database agnostic DB Script to create Northwind Data Model](https://github.com/mrin9/northwind)


http://northwind.servicestack.net/
https://www.hanselman.com/blog/ExploringServiceStacksSimpleAndFastWebServicesOnNETCore.aspx


https://dzone.com/articles/migrating-a-northwind-database-to-nosql-database

Crow's Foot Notation
https://www.codeproject.com/Articles/878359/Data-Modelling-using-ERD-with-Crow-Foot-Notation

Основные таблицы базы данных Northwind представлены на схеме базы данных:
[Northwind Database Schema](http://merc.tv/img/fig/Northwind_diagram.jpg)


https://dzone.com/articles/collection-sql-server-sample-databases

sql tutorial
https://www.zentut.com/sql-tutorial/%20-

4. Найдите в схеме базы данных примеры (если они есть) 1NF, 2NF, 3NF, BCNF, 4NF, 5NF.

* Гудов, Завозкин, Пфайф. Учебное пособие ["Базы данных"](http://unesco.kemsu.ru/study_work/method/DB/book/index.html)
* Сабитов, Пирогов. Учебный курс ["Введение в СУБД"](https://cmd.inp.nsk.su/~pirogov/DB/slides)