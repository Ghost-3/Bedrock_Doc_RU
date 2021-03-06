# Документация по сущностям - `in_lava`

Возвращает true, если объект находится в лаве.

## Параметры

> Примечание
> 
> `in_lava` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `in_lava` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

### value

| Имя   | Значение по умолчанию | Тип    | Описание                            |
|-------|-----------------------|--------|-------------------------------------|
| value | true               | Boolean | (Необязательно) true или false. |

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
{ "test": "in_lava", "subject": "self", "operator": "equals", "value": "true" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "in_lava" }
```

## Примеры сущностей

### Хоглин

``` json
"zombification_sensor": {
  "minecraft:environment_sensor": {
    "triggers": {
      "filters": {
        "test": "in_nether",
        "subject": "self",
        "operator": "==",
        "value": false
      },
      "event": "start_zombification_event"
    }
  }
},
```

## Ванильные сущности, использующие `in_lava`

+ [Хоглин](../../../../Others/Entities/hoglin.md)
+ [Брутальный пиглин](../../../../Others/Entities/piglin_brute.md)
+ [Пиглин](../../../../Others/Entities/piglin.md)
