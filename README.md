# Консольная система учета деталей
Данная система предназначена для гибкого учета хранимых деталей, различных предметов и инструментов.

Данная система оперирует двумя основными понятиями:
 - Элемент
 - Хранилище

Элемент - Это любая деталь, предмет, инструмент, который пользователь хранит в системе. Элемент имеет три поля:
 - Уникальный ID - для однозначного определения элемента в системе
 - Название - Любая стока, характеризующая элемент. Может представлять собой название элемента, описание, part number, уникальный номер изделия и т.д. Содержание этого поля полностью определяется пользователем. В системе не допускаются элементы с одинаковыми названиями.
 - Количество элементов.

Хранилище - это любая система, емкость, коробка, стеллаж, полка, которая физически может хранить элементы и другие хранилища. Например, хранилище Шкаф может хранить в себе хранилище Коробка и хранилище Кассетница. В свою очередь хранилище Коробка и Кассетница могут содержать в себе другие хранилища и элементы.
Любое количество элементов может хранится в любом хранилище. Один и тот же тип элемента может находиться в разных хранилищах. Например 100 штук Резисторов 10 кОм могут лежать в хранилище Кассетница и 5 штук таких же Резисторов 10 кОм могут лежать в хранилище Стол. Стол в своб очередь может находится в хранилище Рабочий кабинет.
Хранилища образую собой древовидную структуру, где каждое хранилище имеет одного родителя (кроме самого старшего) и любое количество детей. Самое старшее хранилище в поле ID Родителя должно содержать 0.
Пользователь может создавать элементы и хранилища, назначая им имена. Для хранилища нужно назначить так же хранилище-родитель, в котором он будет находится.
Пользователь может добавлять элементы в хранилище, забирать элементы из хранилища, перемещать элементы между хранилищами, просматривать остаток элементов в хранилищах, проверять какие элементы лежат в заданном хранилище.
Пользователь может указывать на определенный элемент или хранилище по его уникальному ID или Имени.

## Команды

### Поиск
```
 - search -name STRING - получить все элементы, в названии которых содержится STRING
```
### Работа с хранилищами
```
 - storage --add --name STRING --parent INT - добавить хранилище с именем STRING и родителем INT
 - storage --view --id INT - просмотреть содержание хранилища с ID INT
 - storage --move --id INT --parentid INT - переместить хранилище
```
### Работа с элементами
```
 - item --view --name STRING - просмотреть наличие элемента с именем STRING в хранилищах
 - item --view --id INT - просмотреть наличие элемента с ID INT в хранилищах

 - item --create STRING - создать элемент
 - item --create STRING --id INT2 -quantity INT3 - создать элемент и добавить в хранилище
 - item --add --name STRING1 --id INT1 --storageid INT2 -quantity INT3
 - item --remove --name STRING1 --id INT1 --storageid INT2 -quantity INT3
 - item --move --name STRING1 --id INT1 --storageidsrc INT2 --storageiddst INT3 -quantity INT4
```
### Работа с деревом хранилищ
```
 - tree --storageid INT2 - построить дерево для хранилища
```
### Вспомогательные функции
```
 - status - общая информация
 - help - справка
 - version
```
## TODO

### В модуль работы с БД
 - Empty

### Основная логика приложения
 - Отображение дерева всех хранилищ
 - Вывод основного статуса программы (что выводить?)
 - При создании хранилища передавать желаемый ID
 - Поиск всех доступных хранилищ по имени
