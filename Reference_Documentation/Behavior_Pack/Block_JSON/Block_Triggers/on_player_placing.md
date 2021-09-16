# Документация по блокам - minecraft:on_player_placing

`minecraft:on_player_placing` - это триггер события, когда актер, отмеченный как игрок, размещает блок в мире.

## Параметры

`minecraft:on_player_placing` может использовать следующие параметры

| Имя                                                 | Значение по умолчанию | Тип    | Описание                                                 |
|-----------------------------------------------------|-----------------------|--------|----------------------------------------------------------|
| condition                                           | not set               | String | Условие события, которое должно быть выполнено на блоке. |
| event                                               | not set               | String | Событие, выполняемое на блоке.                           |
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | String | Цель события, выполняемого на блоке.                     |

## Пример

``` json
"minecraft:on_player_placing":{
    "condition": "query.block_property(custom:property) == true", // пользовательское условие
    "event" : "i_put_the_block_down", // пользовательское событие
    "target": "self"
}
```
