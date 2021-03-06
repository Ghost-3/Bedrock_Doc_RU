# Документация по сущностям - `is_climbing`

Возвращает true, если сущность карабкается.

## Параметры

> Примечание
> 
> `is_climbing` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `is_climbing` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

### value

| Имя   | Значение по умолчанию | Тип     | Описание                        |
|-------|-----------------------|---------|---------------------------------|
| value | true                  | Boolean | (Необязательно) true или false. |

### subject

| Параметры | Описание                                               |
|-----------|--------------------------------------------------------|
| block     | Блок, участвующий во взаимодействии.                   |
| damager   | Повреждающий агент, участвующий во взаимодействии.     |
| other     | Другой участник взаимодействия, не вызывающий абонент. |
| parent    | Текущий родитель вызывающего.                          |
| player    | Игрок, участвующий во взаимодействии.                  |
| self      | Сущность или объект, вызывающий тест.                  |
| target    | Текущая цель вызывающего.                              |

### operator

| Параметры | Описание                             |
|-----------|--------------------------------------|
| !=        | Проверка на неравенство.             |
| <         | Тест на меньше значения.             |
| <=        | Тест на меньше или равное значение.  |
| <>        | Тест на неравенство.                 |
| =         | Тест на равенство.                   |
| ==        | Тест на равенство.                   |
| \>        | Тест на большее значение.            |
| >=        | Тест на большее или равное значение. |
| equals    | Тест на равенство.                   |
| not       | Тест на неравенство.                 |

## Примеры

### Полный

``` json
{ "test": "is_climbing", "subject": "self", "operator": "equals", "value": "true" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "is_climbing" }
```

## Примеры сущностей

В настоящее время ни одна сущность не использует `is_climbing`.

## Ванильные сущности, использующие `is_climbing`

В настоящее время ни одна сущность не использует `is_climbing`.
