# Документация сущности - has_damage

Возвращает true, если объект получает названный тип повреждения.

## Параметры

| Имя   | Значение по умолчанию | Тип    | Описание                     |
|-------|-----------------------|--------|------------------------------|
| value | not set               | String | Тип повреждения для проверки |

### Список типов повреждений

Ниже приведен список типов повреждений, которые могут быть использованы для строки `value`.

| Параметры        | Описание                                          |
|------------------|---------------------------------------------------|
| anvil            |                                                   |
| attack           |                                                   |
| block_explosion  |                                                   |
| contact          |                                                   |
| drowning         |                                                   |
| entity_explosion |                                                   |
| fall             |                                                   |
| falling_block    |                                                   |
| fatal            | Любой урон, в результате которого объект умирает. |
| fire             |                                                   |
| fire_tick        |                                                   |
| fly_into_wall    |                                                   |
| lava             |                                                   |
| magic            |                                                   |
| none             |                                                   |
| override         |                                                   |
| piston           |                                                   |
| projectile       |                                                   |
| stalactite       |                                                   |
| stalagmite       |                                                   |
| starve           |                                                   |
| suffocation      |                                                   |
| suicide          |                                                   |
| thorns           |                                                   |
| void             |                                                   |
| wither           |                                                   |

> Примечание
> 
> `has_ability` может также использовать параметры `subject` и [operator](../../../../Others/Operators.md), но они необязательны.

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
| \>         | Тест на большее значение.            |
| >=        | Тест на большее или равное значение. |
| equals    | Тест на равенство.                   |
| not       | Тест на неравенство.                 |

## Примеры

### Полный

``` json
{ "test": "has_damage", "subject": "self", "operator": "equals", "value": "fatal" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "has_damage", "value": "fatal" }
```

## Примеры сущностей

### Разбойник

``` json
"minecraft:damage_sensor": {
  "triggers": {
    "on_damage": {
      "filters": {
        "all_of": [
          {
            "test": "has_damage",
            "value": "fatal"
          },
          {
            "test": "is_family",
            "subject": "other",
            "value": "player"
          }
        ]
      },
```

### Житель

``` json
"minecraft:damage_sensor": {
  "triggers": [
    {
      "on_damage": {
        "filters": { "test" :  "is_family", "subject" : "other", "value" :  "lightning" },
        "event": "become_witch"
      },
      "deals_damage": false
    },
    {
      "on_damage": {
        "filters": {
          "any_of": [
            {"test": "is_family", "subject": "other", "value": "zombie"},
            {"test": "is_family", "subject": "other", "value": "husk"}
          ],
          "all_of": [
            {"test": "has_damage", "value": "fatal"}
          ]
        },
        "event": "become_zombie"
      }
    }
  ]
},
```

## Ванильные сущности, использующие `has_damage`

+ [Разбойник](../../../../Others/Entities/pillager.md)
+ [Житель V2](../../../../Others/Entities/villager_v2.md)
+ [Житель](../../../../Others/Entities/villager.md)
+ [Поборник](../../../../Others/Entities/vindicator.md)
