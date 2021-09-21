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

### Creeper

``` json
"minecraft:biome_filter": {
  "test": "has_biome_tag", "operator":"==", "value": "monster"
}
```

## Ванильные сущности, использующие `has_biome_tag`

+ [bat](../../../../Others/Entities/bat.md)
+ [bee](../../../../Others/Entities/bee.md)
+ [chicken](../../../../Others/Entities/chicken.md)
+ [cod](../../../../Others/Spawn_Rules/cod.md)
+ [cow](../../../../Others/Entities/cow.md)
+ [creeper](../../../../Others/Entities/creeper.md)
+ [dolphin](../../../../Others/Entities/dolphin.md)
+ [donkey](../../../../Others/Entities/donkey.md)
+ [drowned](../../../../Others/Entities/drowned.md)
+ [enderman](../../../../Others/Entities/enderman.md)
+ [fox](../../../../Others/Entities/fox.md)
+ [glow_squid](../../../../Others/Entities/glow_squid.md)
+ [ghast](../../../../Others/Entities/ghast.md)
+ [hoglin](../../../../Others/Entities/hoglin.md)
+ [horse](../../../../Others/Entities/horse.md)
+ [husk](../../../../Others/Entities/husk.md)
+ [llama](../../../../Others/Entities/llama.md)
+ [magma_cube](../../../../Others/Entities/magma_cube.md)
+ [mooshroom](../../../../Others/Entities/mooshroom.md)
+ [ocelot](../../../../Others/Entities/ocelot.md)
+ [panda](../../../../Others/Entities/panda.md)
+ [parrot](../../../../Others/Entities/parrot.md)
+ [phantom](../../../../Others/Entities/phantom.md)
+ [pig](../../../../Others/Entities/pig.md)
+ [piglin](../../../../Others/Entities/piglin.md)
+ [pillager_patrol](../../../../Others/Spawn_Rules/pillager_patrol.md)
+ [polar_bear](../../../../Others/Entities/polar_bear.md)
+ [pufferfish](../../../../Others/Entities/pufferfish.md)
+ [rabbit](../../../../Others/Entities/rabbit.md)
+ [salmon](../../../../Others/Entities/salmon.md)
+ [sheep](../../../../Others/Entities/sheep.md)
+ [skeleton](../../../../Others/Entities/skeleton.md)
+ [slime](../../../../Others/Entities/slime.md)
+ [spider](../../../../Others/Entities/spider.md)
+ [squid](../../../../Others/Entities/squid.md)
+ [stray](../../../../Others/Entities/stray.md)
+ [strider](../../../../Others/Entities/strider.md)
+ [tropicalfish](../../../../Others/Entities/tropicalfish.md)
+ [turtle](../../../../Others/Entities/turtle.md)
+ [witch](../../../../Others/Entities/witch.md)
+ [wolf](../../../../Others/Entities/wolf.md)
+ [zombie_pigman](../../../../Others/Entities/zombie_pigman.md)
+ [zombie](../../../../Others/Entities/zombie.md)
