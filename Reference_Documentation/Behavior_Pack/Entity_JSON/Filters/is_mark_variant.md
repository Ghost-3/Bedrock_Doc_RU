# Документация по сущностям - `is_mark_variant`

Возвращает true, если объект является номером предоставленного варианта марки.

## Параметры

> Примечание
> 
> `is_mark_variant` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `is_mark_variant` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

### value

| Имя   | Значение по умолчанию | Тип    | Описание                            |
|-------|-----------------------|--------|-------------------------------------|
| value | not set               | Integer | (Обязательно) Целочисленное значение. |

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
{ "test": "is_mark_variant", "subject": "self", "operator": "equals", "value": "0" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "is_mark_variant", "value": "0" }
```

## Примеры сущностей

### Лама

``` json
"minecraft:breedable": {
    "require_tame": true,
    "inherit_tamed": false,
    "love_filters": { "test": "is_mark_variant", "subject": "self", "operator": "!=", "value": 1 }, // Ламы странствующих торговцев не могут влюбиться
    "breeds_with": {
      "mate_type": "minecraft:llama",
      "baby_type": "minecraft:llama",
      "breed_event": {
        "event": "minecraft:entity_born",
        "target": "baby"
      }
    },
    "breed_items": [ "hay_block" ]
  }
},
```

### Житель v2

``` json
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 1 },
    "add": { "component_groups": [ "desert_villager" ] }
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 2 },
    "add": { "component_groups": [ "jungle_villager" ] }
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 3 },
    "add": { "component_groups": [ "savanna_villager" ] }
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 4 },
    "add": { "component_groups": [ "snow_villager" ] }
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 5 },
    "add": { "component_groups": [ "swamp_villager" ] }
},
{
    "filters": { "test": "is_mark_variant", "subject": "other", "value": 6 },
```

## Ванильные сущности, использующие `is_mark_variant`

+ [Лама](../../../../Others/Entities/llama.md)
+ [Грибная корова](../../../../Others/Entities/mooshroom.md)
+ [Житель v2](../../../../Others/Entities/villager_v2.md)
+ [Зомби-житель v2](../../../../Others/Entities/zombie_villager_v2.md)
