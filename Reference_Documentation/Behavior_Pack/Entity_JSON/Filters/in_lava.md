# Документация по сущностям - `in_lava`

Возвращает true, если объект находится в лаве.

## Параметры

> Примечание
> 
> `in_lava` **не** требует никаких параметров для правильной работы. Его можно использовать как самостоятельный фильтр.
> 
> `in_lava` также может использовать параметры `subject`, [operator](../../../../Others/Operators.md) и `value`.

### value

| Имя   | Значение по умолчанию | Тип     | Описание                            |
|-------|-----------------------|---------|-------------------------------------|
| value | true                  | Boolean | (Необязательно) true или false.     |

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

### Зомби

``` json
"minecraft:hurt_on_condition": {
  "damage_conditions": [
    {
      "filters": { "test": "in_lava", "subject": "self", "operator": "==", "value": true },
      "cause": "lava",
      "damage_per_tick": 4
    }
  ]
},
```

## Ванильные сущности, использующие `in_lava`

+ [Стрела](../../../../Others/Entities/arrow.md)
+ [Летучая Мышь](../../../../Others/Entities/bat.md)
+ [Пчела](../../../../Others/Entities/bee.md)
+ [Лодка](../../../../Others/Entities/boat.md)
+ [Кошка](../../../../Others/Entities/cat.md)
+ [Пещерный паук](../../../../Others/Entities/cave_spider.md)
+ [Курица](../../../../Others/Entities/chicken.md)
+ [Корова](../../../../Others/Entities/cow.md)
+ [Крипер](../../../../Others/Entities/creeper.md)
+ [Дельфин](../../../../Others/Entities/dolphin.md)
+ [Осёл](../../../../Others/Entities/donkey.md)
+ [Утопленник](../../../../Others/Entities/drowned.md)
+ [Древний страж](../../../../Others/Entities/elder_guardian.md)
+ [Странник Края](../../../../Others/Entities/enderman.md)
+ [Чешуйница Края](../../../../Others/Entities/endermite.md)
+ [Вызыватель](../../../../Others/Entities/evocation_illager.md)
+ [Рыба](../../../../Others/Entities/fish.md)
+ [Светящийся спрут](../../../../Others/Entities/glow_squid.md)
+ [Страж](../../../../Others/Entities/guardian.md)
+ [Хоглин](../../../../Others/Entities/hoglin.md)
+ [Лошадь](../../../../Others/Entities/horse.md)
+ [Кадавр](../../../../Others/Entities/husk.md)
+ [Железный голем](../../../../Others/Entities/iron_golem.md)
+ [Лама](../../../../Others/Entities/llama.md)
+ [Грибная корова](../../../../Others/Entities/mooshroom.md)
+ [Мул](../../../../Others/Entities/mule.md)
+ [Оцелот](../../../../Others/Entities/ocelot.md)
+ [Панда](../../../../Others/Entities/panda.md)
+ [Попугай](../../../../Others/Entities/parrot.md)
+ [Фантом](../../../../Others/Entities/phantom.md)
+ [Свинья](../../../../Others/Entities/pig.md)
+ [Брутальный пиглин](../../../../Others/Entities/piglin_brute.md)
+ [Пиглин](../../../../Others/Entities/piglin.md)
+ [Разбойник](../../../../Others/Entities/pillager.md)
+ [Игрок](../../../../Others/Entities/player.md)
+ [Белый медведь](../../../../Others/Entities/polar_bear.md)
+ [Иглобрюх](../../../../Others/Entities/pufferfish.md)
+ [Кролик](../../../../Others/Entities/rabbit.md)
+ [Разоритель](../../../../Others/Entities/ravager.md)
+ [Лосось](../../../../Others/Entities/salmon.md)
+ [Овца](../../../../Others/Entities/sheep.md)
+ [Шалкер](../../../../Others/Entities/shulker.md)
+ [Чешуйница](../../../../Others/Entities/silverfish.md)
+ [Лошадь-скелет](../../../../Others/Entities/skeleton_horse.md)
+ [Скелет](../../../../Others/Entities/skeleton.md)
+ [Слизень](../../../../Others/Entities/slime.md)
+ [Снежный голем](../../../../Others/Entities/snow_golem.md)
+ [Паук](../../../../Others/Entities/spider.md)
+ [Спрут](../../../../Others/Entities/squid.md)
+ [Зимогор](../../../../Others/Entities/stray.md)
+ [Страйдер](../../../../Others/Entities/strider.md)
+ [Камера](../../../../Others/Entities/tripod_camera.md)
+ [Тропическая рыба](../../../../Others/Entities/tropicalfish.md)
+ [Черепаха](../../../../Others/Entities/turtle.md)
+ [Житель v2](../../../../Others/Entities/villager_v2.md)
+ [Житель](../../../../Others/Entities/villager.md)
+ [Поборник](../../../../Others/Entities/vindicator.md)
+ [Странствующий торговец](../../../../Others/Entities/wandering_trader.md)
+ [Ведьма](../../../../Others/Entities/witch.md)
+ [Волк](../../../../Others/Entities/wolf.md)
+ [Лошадь-зомби](../../../../Others/Entities/zombie_horse.md)
+ [Зомби-житель v2](../../../../Others/Entities/zombie_villager_v2.md)
+ [Зомби-житель](../../../../Others/Entities/zombie_villager.md)
+ [Зомби](../../../../Others/Entities/zombie.md)
