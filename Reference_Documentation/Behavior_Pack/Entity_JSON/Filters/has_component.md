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

### Зомби-Человек

``` json
"events": {
  "minecraft:entity_transformed": {
    "sequence": [
      // Превращает маленькую Свинью в маленького Зомби-Человека
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
      // Превращает взрослую Свинью во взрослого Зомби-Человека
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

+ [Пчела](../../../../Others/Entities/bee.md)
+ [Кошка](../../../../Others/Entities/cat.md)
+ [Крипер](../../../../Others/Entities/creeper.md)
+ [Вызыватель](../../../../Others/Entities/evocation_illager.md)
+ [Хоглин](../../../../Others/Entities/hoglin.md)
+ [Кадавр](../../../../Others/Entities/husk.md)
+ [Лама](../../../../Others/Entities/llama.md)
+ [Грибная корова](../../../../Others/Entities/mooshroom.md)
+ [Панда](../../../../Others/Entities/panda.md)
+ [Пиглин](../../../../Others/Entities/piglin.md)
+ [Разбойник](../../../../Others/Entities/pillager.md)
+ [Кролик](../../../../Others/Entities/rabbit.md)
+ [Разоритель](../../../../Others/Entities/ravager.md)
+ [Овца](../../../../Others/Entities/sheep.md)
+ [Снежный Голем](../../../../Others/Entities/snow_golem.md)
+ [Вагонетка с динамитом](../../../../Others/Entities/tnt_minecart.md)
+ [Досаждатель](../../../../Others/Entities/vex.md)
+ [Житель V2](../../../../Others/Entities/villager_v2.md)
+ [Житель](../../../../Others/Entities/villager.md)
+ [Поборник](../../../../Others/Entities/vindicator.md)
+ [Странствующий Торговец](../../../../Others/Entities/wandering_trader.md)
+ [Зогин](../../../../Others/Entities/zoglin.md)
+ [Зомби Житель v2](../../../../Others/Entities/zombie_villager_v2.md)
+ [Зомби Житель](../../../../Others/Entities/zombie_villager.md)
+ [Зомби](../../../../Others/Entities/zombie.md)
