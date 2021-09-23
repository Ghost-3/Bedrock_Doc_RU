# Документация сущности - has_biome_tag

Проверяет, имеет ли биом, в котором находится субъект, указанный тег.

## Параметры

Имя Значение по умолчанию Тип Описание
value not set String (Обязательно) Метка для поиска

| Имя   | Значение по умолчанию | Тип    | Описание                       |
|-------|-----------------------|--------|--------------------------------|
| value | not set               | String | (Обязательно) Метка для поиска |

> Примечание
> 
> `has_biome_tag` может также использовать параметры `subject` и [operator](../../../../Others/Operators.md), но они необязательны.

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
{ "test": "has_biome_tag", "subject": "self", "operator": "equals", "value": " " }
```

### Короткий (с использованием значений по умолчанию)

``` json
{ "test": "has_biome_tag", "value": " " }
```

## Примеры сущностей

### Крипер

``` json
"minecraft:biome_filter": {
  "test": "has_biome_tag", "operator":"==", "value": "monster"
}
```

## Ванильные сущности, использующие `has_biome_tag`

+ [Летучая мышь](../../../../Others/Entities/bat.md)
+ [Пчела](../../../../Others/Entities/bee.md)
+ [Курица](../../../../Others/Entities/chicken.md)
+ [Треска](../../../../Others/Spawn_Rules/cod.md)
+ [Корова](../../../../Others/Entities/cow.md)
+ [Крипер](../../../../Others/Entities/creeper.md)
+ [Дельфин](../../../../Others/Entities/dolphin.md)
+ [Осёл](../../../../Others/Entities/donkey.md)
+ [Утопленник](../../../../Others/Entities/drowned.md)
+ [Странник Края](../../../../Others/Entities/enderman.md)
+ [Лиса](../../../../Others/Entities/fox.md)
+ [Светящийся Спрут](../../../../Others/Entities/glow_squid.md)
+ [Гаст](../../../../Others/Entities/ghast.md)
+ [Хоглин](../../../../Others/Entities/hoglin.md)
+ [Лошадь](../../../../Others/Entities/horse.md)
+ [Кадавр](../../../../Others/Entities/husk.md)
+ [Лама](../../../../Others/Entities/llama.md)
+ [Лавовый Куб](../../../../Others/Entities/magma_cube.md)
+ [Грибная корова](../../../../Others/Entities/mooshroom.md)
+ [Оцелот](../../../../Others/Entities/ocelot.md)
+ [Панда](../../../../Others/Entities/panda.md)
+ [Попугай](../../../../Others/Entities/parrot.md)
+ [Фантом](../../../../Others/Entities/phantom.md)
+ [Свинья](../../../../Others/Entities/pig.md)
+ [Пиглин](../../../../Others/Entities/piglin.md)
+ [Патруль Разбойников](../../../../Others/Spawn_Rules/pillager_patrol.md)
+ [Белый медведь](../../../../Others/Entities/polar_bear.md)
+ [Иглобрюх](../../../../Others/Entities/pufferfish.md)
+ [Кролик](../../../../Others/Entities/rabbit.md)
+ [Лосось](../../../../Others/Entities/salmon.md)
+ [Овца](../../../../Others/Entities/sheep.md)
+ [Скелет](../../../../Others/Entities/skeleton.md)
+ [Слизень](../../../../Others/Entities/slime.md)
+ [Паук](../../../../Others/Entities/spider.md)
+ [Спрут](../../../../Others/Entities/squid.md)
+ [Зимого](../../../../Others/Entities/stray.md)
+ [Страйдер](../../../../Others/Entities/strider.md)
+ [Тропическая рыба](../../../../Others/Entities/tropicalfish.md)
+ [Черепаха](../../../../Others/Entities/turtle.md)
+ [Ведьма](../../../../Others/Entities/witch.md)
+ [Волк](../../../../Others/Entities/wolf.md)
+ [Зомби-Человек](../../../../Others/Entities/zombie_pigman.md)
+ [Зомби](../../../../Others/Entities/zombie.md)
