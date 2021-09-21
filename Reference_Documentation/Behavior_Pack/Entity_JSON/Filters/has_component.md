# Документация по сущностям - has_component

Возвращает true, если объект содержит названный компонент.

## Параметры

| Имя   | Значение по умолчанию | Тип    | Описание                                            |
|-------|-----------------------|--------|-----------------------------------------------------|
| value | not set               | String | (Обязательно) Имя компонента, который нужно искать. |

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
| >         | Тест на большее значение.            |
| >=        | Тест на большее или равное значение. |
| equals    | Тест на равенство.                   |
| not       | Тест на неравенство.                 |

## Примеры

### Полный

``` json
{ "test": "has_component", "subject": "self", "operator": "equals", "value": "minecraft:explode" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "has_component", "value": "minecraft:explode" }
```

## Примеры сущностей

### zombie pigman

``` json
"events": {
  "minecraft:entity_transformed": {
    "sequence": [
      // Transform baby pig to baby zombie pigman
      {
        "filters": {
          "test": "has_component",
          "subject": "other",
          "value": "minecraft:is_baby"
        },
        "add": {
          "component_groups": [
            "minecraft:pig_zombie_baby",
            "minecraft:pig_zombie_calm"
          ]
        }
      },
      // Transform adult pig to adult zombie pigman
      {
        "filters": {
          "test": "has_component",
          "subject": "other",
          "operator": "!=",
          "value": "minecraft:is_baby"
        },
        "add": {
          "component_groups": [
            "minecraft:pig_zombie_adult",
            "minecraft:pig_zombie_calm"
          ]
        }
      }
```

## Ванильные сущности, использующие `has_ability`

+ [bee](../../../../Others/Entities/bee.md)
+ [cat](../../../../Others/Entities/cat.md)
+ [creeper](../../../../Others/Entities/creeper.md)
+ [evocation_illager](../../../../Others/Entities/evocation_illager.md)
+ [hoglin](../../../../Others/Entities/hoglin.md)
+ [husk](../../../../Others/Entities/husk.md)
+ [llama](../../../../Others/Entities/llama.md)
+ [mooshroom](../../../../Others/Entities/mooshroom.md)
+ [panda](../../../../Others/Entities/panda.md)
+ [piglin](../../../../Others/Entities/piglin.md)
+ [pillager](../../../../Others/Entities/pillager.md)
+ [rabbit](../../../../Others/Entities/rabbit.md)
+ [ravager](../../../../Others/Entities/ravager.md)
+ [sheep](../../../../Others/Entities/sheep.md)
+ [snow_golem](../../../../Others/Entities/snow_golem.md)
+ [tnt_minecart](../../../../Others/Entities/tnt_minecart.md)
+ [vex](../../../../Others/Entities/vex.md)
+ [villager_V2](../../../../Others/Entities/villager_v2.md)
+ [villager](../../../../Others/Entities/villager.md)
+ [vindicator](../../../../Others/Entities/vindicator.md)
+ [wandering_trader](../../../../Others/Entities/wandering_trader.md)
+ [zoglin](../../../../Others/Entities/zoglin.md)
+ [zombie_villager_v2](../../../../Others/Entities/zombie_villager_v2.md)
+ [zombie_villager](../../../../Others/Entities/zombie_villager.md)
+ [zombie](../../../../Others/Entities/zombie.md)
