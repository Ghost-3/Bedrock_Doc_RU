# Документация по блокам - minecraft:on_player_destroyed

`minecraft:on_player_destroyed` - это триггер события, когда актер, отмеченный как игрок, уничтожает блок.

## Параметры

`minecraft:on_player_destroyed` может использовать следующие параметры

| Имя       | Значение по умолчанию | Тип    | Описание                                                 |
|-----------|-----------------------|--------|----------------------------------------------------------|
| condition | not set               | String | Условие события, которое должно быть выполнено на блоке. |
| event     | not set               | String | Событие, выполняемое на блоке.                           |
| target    | self                  | String | Цель события, выполняемого на блоке.                     |

## Пример

``` json
"minecraft:on_player_destroyed":{
    "condition": "query.block_property(custom:property) == true", // пользовательское условие
    "event" : "this_is_my_block", // пользовательское событие
    "target": "self"
}
```
