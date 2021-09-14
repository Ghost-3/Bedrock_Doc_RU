# Документация по блокам - minecraft:breathability

`minecraft:breathability` is a component that sets the breathability of the block, and whether it's treated as a solid block or a block of air.

## Default Parameter

| Значение по умолчанию | Тип        |
|-----------------------|------------|
| solid                 | Enumerator |

## Enumerator

`minecraft:breathability` использует 2 состояния enumerator.

| Имя   | Описание                              |
|-------|---------------------------------------|
| solid | Блок рассматривается как твердый блок |
| air   | Блок рассматривается как воздух       |

## Пример

``` json
"minecraft:breathability": "solid"
```