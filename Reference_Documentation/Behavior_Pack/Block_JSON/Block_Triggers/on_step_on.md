# Документация по блокам - minecraft:on_step_on

`minecraft:on_step_on` - это триггер события, когда актер наступает на блок.

## Параметры

`minecraft:on_step_on` может использовать следующие параметры

| Имя                                                 | Значение по умолчанию | Тип    | Описание                                                 |
|-----------------------------------------------------|-----------------------|--------|----------------------------------------------------------|
| condition                                           | not set               | String | Условие события, которое должно быть выполнено на блоке. |
| event                                               | not set               | String | Событие, выполняемое на блоке.                           |
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | String | Цель события, выполняемого на блоке.                     |

## Пример

``` json
"minecraft:on_step_on":{
    "condition": "query.block_property(custom:is_playing_sound) == false", // пользовательское условие
    "event" : "sound_the_alarm", // пользовательское событие
    "target": "self"
}
```
