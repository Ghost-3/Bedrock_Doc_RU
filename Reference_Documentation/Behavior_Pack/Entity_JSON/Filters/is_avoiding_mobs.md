# Документация по сущностям - `is_avoiding_mobs`

Возвращает true, если объект убегает от других мобов.

## Параметры

> Примечание
> 
> `is_avoiding_mobs` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `is_avoiding_mobs` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

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
{ "test": "is_avoiding_mobs", "subject": "self", "operator": "equals", "value": "true" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "is_avoiding_mobs" }
```

## Примеры сущностей

### Странствующий торговец

``` json
"potions": [
  {
    "id": 7, // Кратковременная невидимость
    "chance": 1.0,
    "filters": {
      "all_of": [
        {
          "any_of": [
            { "test": "hourly_clock_time", "operator": ">=", "value": 18000 },
            { "test": "hourly_clock_time", "operator": "<", "value": 12000 }
          ]
        },
        { "test": "is_visible", "subject": "self", "value": true },
        {
          "any_of": [
            { "test": "is_avoiding_mobs", "subject": "self", "value": true },
            {
              "all_of": [
                { "test": "has_component", "subject": "self", "value": "minecraft:angry" },
                { "test": "is_family", "subject": "target", "operator": "!=", "value": "player" }
              ]
            }
          ]
        }
      ]
    }
  },
```

## Ванильные сущности, использующие `is_avoiding_mobs`

+ [Странствующий торговец](../../../../Others/Entities/wandering_trader.md)

Process finished with exit code 0
