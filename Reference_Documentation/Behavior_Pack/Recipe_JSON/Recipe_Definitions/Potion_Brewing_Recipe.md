# Документация по Рецептам крафта - Рецепты зельеварения

Представляет рецепт, который используется зельеварочной стойкой.

## Параметры

| Название | Тип              | Описание                                                               |
|----------|------------------|------------------------------------------------------------------------|
| input    | зелье            | Входное зелье, используемое в зельеварочном рецепте.                   |
| output   | зелье            | Выходное зелье из рецепта зельеварения.                                |
| reagent  | предмет          | Предмет, используемый в зельеварочном рецепта вместе с входным зельем. |
| tags     | строковый массив | Объекты, которые используют данный рецепт.                             |

## Пример рецепта зельеварения

``` json
{
"format_version": "1.17",
    "minecraft:recipe_brewing_container": {
    "description": {
        "identifier": "minecraft:brew_potion_sulphur"
    },
    "tags": [ "brewing_stand" ],
    "input": "minecraft:potion",
    "reagent": "minecraft:gunpowder",
    "output": "minecraft:splash_potion",
    }
}
```

## Стандартный пример

### Зелье замедленного падения

``` json
{
  "format_version": "1.12",
  "minecraft:recipe_brewing_mix": {
    "description": {
      "identifier": "minecraft:brew_slow_falling_redstone"
    },

    "tags": [ "brewing_stand" ],

    "input": "minecraft:potion_type:slow_falling",
    "reagent": "minecraft:redstone",
    "output": "minecraft:potion_type:long_slow_falling"
  }

}
```

[comment]: <> (Спасибо Foxuk)
