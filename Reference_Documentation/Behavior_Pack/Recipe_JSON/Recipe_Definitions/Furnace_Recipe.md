# Документация по рецептам крафта - Рецепты для печи

Является рецептом крафта, который должен использоваться печью. Входные (`input`) предметы сгорают и превращаются в предметы, указанные в выходных (`output`).

## Параметры

| Название | Тип                | Описание                                             |
|----------|--------------------|------------------------------------------------------|
| input    | параметры предмета | Предметы, используемые как входные для рецепта печи. |
| output   | параметры предмета | Предметы, используемы как выходные для рецепта печи. |
| tags     | строковый массив   | Объекты, которые используют данный рецепт.           |

## Пример рецепта печи

``` json
{
"format_version": "1.17",
"minecraft:recipe_furnace": {
    "description": {
        "identifier": "minecraft:furnace_beef"
        },
    "tags": ["furnace", "smoker", "campfire", "soul_campfire"],
    "input": {
        "item": "minecraft:beef",
        "data": 0,
        "count": 4
        },
    "output ": "minecraft:cooked_beef"
    }
}
```

## Стандартный пример

``` json
{
  "format_version": "1.12",
  "minecraft:recipe_furnace": {
    "description": {
    "identifier": "minecraft:furnace_cobblestone"
    },

    
    "tags": ["furnace"],
    "input": "minecraft:cobblestone",
    "output": "minecraft:stone"
  }
  
}
```

[comment]: <> (Спасибо Foxuk)
