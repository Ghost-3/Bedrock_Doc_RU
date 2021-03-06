# Документация по блокам - minecraft:placement_filte

`minecraft:placement_filter` - это компонент, управляемый `JSON object`, который задает правила, при каких условиях можно размещать блок.

## Параметр по умолчанию

| Значение по умолчанию | Тип         |
|-----------------------|-------------|
| not set               | JSON Object |

## Условия

`minecraft:placement_filter` может использовать следующие условия

| Имя           | Значение по умолчанию | Тип   | Описание                                                                                                                            |
|---------------|-----------------------|-------|-------------------------------------------------------------------------------------------------------------------------------------|
| allowed_faces | not set               | Array | Список любых из следующих строк: up, down, north, south, east, west, side, all                                                      |
| block_filter  | not set               | Array | Список блоков (можно использовать теги для их указания), против которых может быть размещен данный блок в направлении allowed_faces |

## Пример

``` json
"minecraft:placement_filter":{
    "allowed_faces": ["вверх", "вниз", "вбок"],
    "block_filter": ["grass", "dirt"]
}
```
