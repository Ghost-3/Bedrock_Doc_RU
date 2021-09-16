# Документация по блокам - minecraft:on_step_off

`minecraft:on_step_off` - это триггер события, когда актер выходит из блока.

## Параметры

`minecraft:on_step_off` может использовать следующие параметры.

| Имя                                                 | Значение по умолчанию | Тип    | Описание                                                 |
|-----------------------------------------------------|-----------------------|--------|----------------------------------------------------------|
| condition                                           | not set               | String | Условие события, которое должно быть выполнено на блоке. |
| event                                               | not set               | String | Событие, выполняемое на блоке.                           |
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | String | Цель события, выполняемого на блоке.                     |

## Пример

``` json
"minecraft:on_step_off":{
    "condition": "query.block_property(custom:is_playing_sound) == true", // пользовательское условие
    "event" : "disable_the_alarm", // пользовательское событие
    "target": "self"
}
```
