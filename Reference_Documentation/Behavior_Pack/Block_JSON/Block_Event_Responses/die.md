# Документация по блокам - умереть

`die` - это реакция события, которая убивает цель.

## Дополнительные параметры

`die` может использовать следующие параметры

| Имя                                                 | Значение по умолчанию | Тип              | Описание                         |
|-----------------------------------------------------|-----------------------|------------------|----------------------------------|
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | Minecraft Filter | Целевой контекст для выполнения. |

## Пример

``` json
"die" : {
    "target" : { "test": "random_chance", "value": "1"} //50% шанс
}
```
