# Документация по Рецептам крафта - Бесформенные рецепты

Является бесформенным рецептом крафта.

> Примечание
> 
> В отличие от [Форменного рецепта](Shaped_Recipe.md), шаблон и ключ не используются в Бесформенном рецепте.

## Параметры

| Название    | Тип                        | Описание                                                       |
|-------------|----------------------------|----------------------------------------------------------------|
| ingredients | массив параметров предмета | Предметы используются как входные (не имея формы) для рецепта. |
| priority    | целое число                | Приоритет, с которым рецепт будет выбран перед другими.        |
| result      | массив параметров предмета | Эти предметы являются результатом.                             |

## Пример бесформенного рецепта

``` json
{
"format_version": "1.17",
    "minecraft:recipe_shapeless": {
        "description": {
            "identifier": "minecraft:firecharge_coal_sulphur"
        },
     "priority": 0,
     "ingredients": {
        "item": "minecraft:fireball",
        "data": 0,
        "count": 4
     },
    "result": {
        "item": "minecraft:blaze_powder",
        "data": 4
        }
    }
}
```

## Стандартный пример

### Огненный порошок

``` json
{
  "format_version": "1.12",
  "minecraft:recipe_shapeless": {
    "description": {
    "identifier": "minecraft:blaze_powder"
    },

    
    "tags": [ "crafting_table" ],
    "ingredients": [
      {
        "item": "minecraft:blaze_rod"
      }
    ],
    "result": {
      "item": "minecraft:blaze_powder",
      "count": 2
    }
  }
}
```

[comment]: <> (Спасибо Foxuk)
