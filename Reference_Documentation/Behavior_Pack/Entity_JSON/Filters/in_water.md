# Документация по сущностям - `in_water`

Возвращает true, если объект находится в воде.

## Параметры

> Примечание
> 
> `in_water` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `in_water` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

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
{ "test": "in_water", "subject": "self", "operator": "equals", "value": "true" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "in_water" }
```

## Примеры сущностей

### Аксолотль

``` json
"filters": { "test": "in_water_or_rain", "operator": "!=", "value": true },
```

### Оцелот

``` json
"minecraft:behavior.nearest_attackable_target": {
  "priority": 1,
  "reselect_targets": true,
  "entity_types": [
    {
      "filters": {
        "test": "is_family",
        "subject": "other",
        "value": "chicken"
      },
      "max_dist": 8
    },
    {
      "filters": {
        "all_of": [
          {
            "test": "is_family",
            "subject": "other",
            "value": "baby_turtle"
          },
          {
            "test": "in_water",
            "subject": "other",
            "operator": "!=",
            "value": true
          }
        ]
      },
      "max_dist": 8
    }
  ]
},
```

## Ванильные сущности, использующие `in_water`

+ [Аксолотль](../../../../Others/Entities/axolotl.md)
+ [Кошка](../../../../Others/Entities/cat.md)
+ [Дельфин](../../../../Others/Entities/dolphin.md)
+ [Утопленник](../../../../Others/Entities/drowned.md)
+ [Лиса](../../../../Others/Entities/fox.md)
+ [Кадавр](../../../../Others/Entities/husk.md)
+ [Оцелот](../../../../Others/Entities/ocelot.md)
+ [Панда](../../../../Others/Entities/panda.md)
+ [Разбойник](../../../../Others/Entities/pillager.md)
+ [Скелет](../../../../Others/Entities/skeleton.md)
+ [Зимогор](../../../../Others/Entities/stray.md)
+ [Скелет-иссушитель](../../../../Others/Entities/wither_skeleton.md)
+ [Волк](../../../../Others/Entities/wolf.md)
+ [Зомби-житель v2](../../../../Others/Entities/zombie_villager_v2.md)
+ [Зомби-житель](../../../../Others/Entities/zombie_villager.md)
+ [Зомби](../../../../Others/Entities/zombie.md)
