# Документация по блокам - play_sound

`play_sound` - это реакция на событие, которая будет воспроизводить звуковой эффект относительно целевой позиции.

## Дополнительные параметры

`play_sound` может использовать следующие параметры

| Имя                                                 | Значение по умолчанию | Тип              | Описание                         |
|-----------------------------------------------------|-----------------------|------------------|----------------------------------|
| sound                                               | not set               | String           | Имя воспроизводимого звука.      |
| [target](../../Entity_JSON/Filters/Filters_List.md) | self                  | Minecraft Filter | Целевой контекст для выполнения. |

## Пример

``` json
"play_sound":{
    "sound" : "jumpscare",
    "target" : { "test": "random_chance", "value": "2"} //33%
}
```
