# Документация по сущностям - `is_family`

Возвращает true, если объект является членом названного семейства.

## Параметры

| Имя   | Значение по умолчанию | Тип    | Описание                                      |
|-------|-----------------------|--------|-----------------------------------------------|
| value | not set               | String | (Обязательно) Семейство, которое нужно искать |

> Примечание
> 
> `is_family` может также использовать параметры `subject` и [operator](../../../../Others/Operators.md), но они необязательны.

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
{ "test": "is_family", "subject": "self", "operator": "equals", "value": "player" }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "is_family", "value": "player" }
```

## Примеры сущностей

### Стрела

``` json
{
  "filters": {"test": "is_family", "subject": "other", "value": "player"},
  "add": {
    "component_groups" : [ "minecraft:player_arrow" ]
  }
},
```

## Ванильные сущности, использующие `is_family`

+ [Стрела](../../../../Others/Entities/arrow.md)
+ [Пчела](../../../../Others/Entities/bee.md)
+ [Ифрит](../../../../Others/Entities/blaze.md)
+ [Кошка](../../../../Others/Entities/cat.md)
+ [Пещерный паук](../../../../Others/Entities/cave_spider.md)
+ [Корова](../../../../Others/Entities/cow.md)
+ [Крипер](../../../../Others/Entities/creeper.md)
+ [Дельфин](../../../../Others/Entities/dolphin.md)
+ [Осёл](../../../../Others/Entities/donkey.md)
+ [Кислота Края](../../../../Others/Entities/dragon_fireball.md)
+ [Утопленник](../../../../Others/Entities/drowned.md)
+ [Древний страж](../../../../Others/Entities/elder_guardian.md)
+ [Странник Края](../../../../Others/Entities/enderman.md)
+ [Чешуйница Края](../../../../Others/Entities/endermite.md)
+ [Вызыватель](../../../../Others/Entities/evocation_illager.md)
+ [Рыба](../../../../Others/Entities/fish.md)
+ [Лиса](../../../../Others/Entities/fox.md)
+ [Гаст](../../../../Others/Entities/ghast.md)
+ [Страж](../../../../Others/Entities/guardian.md)
+ [Хоглин](../../../../Others/Entities/hoglin.md)
+ [Кадавр](../../../../Others/Entities/husk.md)
+ [Железный голем](../../../../Others/Entities/iron_golem.md)
+ [Лама](../../../../Others/Entities/llama.md)
+ [Лавовый куб](../../../../Others/Entities/magma_cube.md)
+ [Грибная корова](../../../../Others/Entities/mooshroom.md)
+ [Мул](../../../../Others/Entities/mule.md)
+ [Оцелот](../../../../Others/Entities/ocelot.md)
+ [Панда](../../../../Others/Entities/panda.md)
+ [Фантом](../../../../Others/Entities/phantom.md)
+ [Свинья](../../../../Others/Entities/pig.md)
+ [Брутальный пиглин](../../../../Others/Entities/piglin_brute.md)
+ [Пиглин](../../../../Others/Entities/piglin.md)
+ [Разбойник](../../../../Others/Entities/pillager.md)
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
+ [Зимогор](../../../../Others/Entities/stray.md)
+ [Вагонетка с динамитом](../../../../Others/Entities/tnt_minecart.md)
+ [Тропическая рыба](../../../../Others/Entities/tropicalfish.md)
+ [Досаждатель](../../../../Others/Entities/vex.md)
+ [Житель v2](../../../../Others/Entities/villager_v2.md)
+ [Житель](../../../../Others/Entities/villager.md)
+ [Поборник](../../../../Others/Entities/vindicator.md)
+ [Странствующий торговец](../../../../Others/Entities/wandering_trader.md)
+ [Ведьма](../../../../Others/Entities/witch.md)
+ [Скелет-иссушитель](../../../../Others/Entities/wither_skeleton.md)
+ [Иссушитель](../../../../Others/Entities/wither.md)
+ [Волк](../../../../Others/Entities/wolf.md)
+ [Зоглин](../../../../Others/Entities/zoglin.md)
+ [Зомби-житель v2](../../../../Others/Entities/zombie_villager_v2.md)
+ [Зомби-житель](../../../../Others/Entities/zombie_villager.md)
+ [Зомби](../../../../Others/Entities/zombie.md)
