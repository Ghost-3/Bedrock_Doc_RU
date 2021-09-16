# Документация по блокам - minecraft:on_placed

`minecraft:on_placed` - это триггер события, когда актер размещает блок в мире.

## Параметры

`minecraft:on_placed` может использовать следующие параметры

| Имя                                                 | Значение по умолчанию | Тип    | Описание                                                 |
|-----------------------------------------------------|-----------------------|--------|----------------------------------------------------------|
| condition                                           | not set               | String | Условие события, которое должно быть выполнено на блоке. |
| event                                               | not set               | String | Событие, выполняемое на блоке.                           |
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | String | Цель события, выполняемого на блоке.                     |

## Пример

``` json
"minecraft:on_placed":{
    "condition": "query.block_property(custom:normal_facing_up) == true", // пользовательское условие
    "event" : "the_thing_has_been_placed", // пользовательское событие
    "target": "self"
}
```
