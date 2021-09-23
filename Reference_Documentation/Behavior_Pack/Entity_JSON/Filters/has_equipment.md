# Документация сущности - has_equipment

Проверяет наличие именованного предмета в указанном слоте субъекта.

## Параметры

| Имя   | Значение по умолчанию | Тип    | Описание                                         |
|-------|-----------------------|--------|--------------------------------------------------|
| value | not set               | String | (Обязательно) Имя элемента, который нужно искать |

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

### domain

Domain используется для проверки места расположения снаряжения.

**Параметры**:

+ any
+ armor
+ feet
+ hand
+ head
+ leg
+ torso

## Примеры

### Полный

``` json
{ "test": "has_equipment", "subject": "self", "domain": "any", "operator": "equals", "value": "dirt"
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "has_equipment", "value": "dirt" }
```

## Примеры сущностей

### Корова

``` json
"minecraft:interact": {
  "interactions": [
    {
      "on_interact": {
        "filters": {
          "all_of": [
            { "test": "is_family", "subject" : "other", "value" :  "player"},
            { "test": "has_equipment", "domain": "hand", "subject": "other", "value": "bucket:0"}
          ]
        }
      },
      "use_item": true,
      "transform_to_item": "bucket:1",
      "play_sounds": "milk",
      "interact_text": "action.interact.milk"
    }
  ]
}
```

### Мул

``` json
"minecraft:mule_unchested": {
  "minecraft:interact": {
    "interactions": [
      {
        "play_sounds": "armor.equip_generic",
        "on_interact": {
          "filters": {
            "all_of": [
              { "test": "has_equipment", "subject": "other", "domain": "hand", "value": "chest"},
              { "test" :  "is_family", "subject" : "other", "value" :  "player"}
            ]
          },
          "event": "minecraft:on_chest",
          "target": "self"
        },
        "use_item": true,
        "interact_text": "action.interact.attachchest"
      }
    ]
  }
},
```

## Ванильные сущности, использующие `has_equipment`

+ [Корова](../../../../Others/Entities/cow)
+ [Крипер](../../../../Others/Entities/creeper)
+ [Дельфин](../../../../Others/Entities/dolphin)
+ [Осёл](../../../../Others/Entities/donkey)
+ [Жемчуг Края](../../../../Others/Entities/ender_pearl)
+ [Странник Края](../../../../Others/Entities/enderman)
+ [Лама](../../../../Others/Entities/llama)
+ [Грибная Корова](../../../../Others/Entities/mooshroom)
+ [Мул](../../../../Others/Entities/mule)
+ [Свинья](../../../../Others/Entities/pig)
+ [Пиглин](../../../../Others/Entities/piglin)
+ [Овца](../../../../Others/Entities/sheep)
+ [Шалкер](../../../../Others/Entities/shulker)
+ [Снежный Голем](../../../../Others/Entities/snow_golem)
+ [Страйдер](../../../../Others/Entities/strider)
+ [Вагонетка с Динамитом](../../../../Others/Entities/tnt_minecart)
+ [Зомби Житель v2](../../../../Others/Entities/zombie_villager_v2)
+ [Зомби Житель](../../../../Others/Entities/zombie_villager)
