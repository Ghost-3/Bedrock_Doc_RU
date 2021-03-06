# Как добавить пользовательский блок

Пакеты ресурсов и параметров Minecraft позволяют создавать пользовательский контент для своей аудитории.
Пользовательские блоки - это отличный способ для создателей начать добавлять интерактивный контент, с которым могут
взаимодействовать игроки. В этом уроке вы создадите новый блок, который будет называться **блоком холста**, который вы
можете украсить различными текстурами и который может быть размещен игроком.

В этом уроке вы узнаете следующее:

+ Использование JSON для определения нового блока.
+ Назначение текстур новому блоку.
+ К каким моделям поведения и компонентам имеют доступ блоки.
+ Краткое описание **.lang** и его использования для внутриигрового текста.

### Требования

Перед началом этого урока рекомендуется выполнить следующие требования.

+ [Начало разработки дополнений](Getting_Started.md)
+ [Введение в наборы ресурсов](Introduction_to_Resource_Packs.md)
+ [Введение в наборы параметров](Introduction_to_Behavior_Packs.md)
+ Загрузите [Vanilla resource pack](https://aka.ms/resourcepacktemplate)
+ Мир Minecraft с включенным `Holiday Creator Features`.

> Важно!
>
> Holiday Creator Features содержит экспериментальные игровые функции. Как и в случае со всеми экспериментами, вы можете увидеть добавления, удаления и изменения функциональности в версиях Minecraft без существенного предварительного предупреждения.
>
> Чтобы узнать больше об экспериментальных возможностях, пожалуйста, посетите [Экспериментальные возможности в Minecraft: Bedrock Edition](../../Articles/Useful_Knowledge_for_Creators/Experimental_Features_in_Minecraft_Bedrock_Edition.md)

## Настройка JSON-файла ресурсов

Определения сущностей блоков обрабатываются по-другому в пакете ресурсов. Блоки хранятся в одном JSON-файле, который
будет содержать определения для каждого пользовательского блока.

1. Откройте папку с расположением игры **com.mojang**.
2. Дважды щелкните на папке **development_resource_packs**.
3. Дважды щелкните на папке **HelloWorldRP**.
    + Если у вас нет этой папки, обратитесь к учебникам в разделе "Требования".
4. Щелкните правой кнопкой мыши в окне проводника и выберите **Создать**, затем выберите **Текстовый документ**.
5. Задайте имя **blocks.json**.
6. Дважды щелкните на файле **blocks.json**, чтобы открыть его в текстовом редакторе.

### blocks.json

Файл blocks.json устроен аналогично файлу manifest.json и имеет требования для корректной работы. Блок холста будет
использовать пользовательскую текстуру для каждого размера, за исключением верхней и нижней сторон. Эти стороны будут
использовать ванильную текстуру, которая будет перенесена в пакет для использования.

1. Скопируйте/вставьте следующий текст в текстовый редактор.
   ``` json
   {
   "format_version": "1.16.0",
     "helloworld:canvasblock": {
       "textures": {
           "up": "log_oak_top",
           "down": "log_oak_top",
           "side": "canvasblock"
           },
       "sound":"dirt"
       }
   }
   ```
2. Сохраните файл

#### Текстуры и субтекстуры

Как показано в приведенном выше коде JSON, блок canvas использует 2 текстуры. Верхняя и нижняя части используют
существующий файл log_oak_top.png, а другая сторона использует пользовательскую текстуру. Блокам может быть назначена
одна текстура, чтобы покрыть все стороны блока одной и той же текстурой.

`"textures": "canvasblock"`

Текстуры могут быть разбиты на группы подтекстур. `up`, `down`, `side` - это все подтекстуры, которые позволяют
создателю определить, какая сторона получает определенную текстуру. `side` также могут быть разбиты на кардинальные
направления: `north`, `east`, `south`, `west`.

### terrain_texture.json

Когда блок определен в файле **blocks.json**, следующий шаг - связать имена текстур с путем к файлу текстуры. Это делается в файле terrain_texture.json.

1. В **Проводнике** перейдите в папку **HelloWorldRP/textures**.
2. Щелкните правой кнопкой мыши в окне Проводника и выберите **Создать**, затем выберите **Текстовый документ**.
3. Задайте имя **terrain_texture.json**.
4. Дважды щелкните на файле **terrain_texture.json**, чтобы открыть его в текстовом редакторе.
5. Скопируйте и вставьте следующий код:
``` json
{
  "resource_pack_name": "HelloWorldBP",
  "texture_name": "atlas.terrain",
  "padding": 8,
  "num_mip_levels": 4,
  "texture_data": {
    "canvasblock": {
      "textures": "textures/blocks/canvasblock"
    },
    "log_oak_top":{
      "textures": "textures/blocks/log_oak_top"
    }
  }
}
```
6. Сохраните файл

### Текстура холста

![canvasblock.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/customblocks/canvasblock.png)

Текстура блока холста должна быть сгенерирована и помещена в Ресурс-пак. Есть изображение, которое будет предоставлено
для `canvasblock.png`, но не стесняйтесь использовать другую текстуру.

Если вы используете предоставленную:

1. Загрузите файл на свой компьютер.
2. Поместите файл `canvasblock.png` в папку `HelloWorldRP/textures/blocks`.

Если вы создаете пользовательскую:

1. Убедитесь, что значения **Ширина** и **Высота** установлены по 16.
2. Сохраните файл под именем `canvasblock.png` в папке `HelloWorldRP/textures/blocks`.

#### Добавление log_oak_top.png

Файл `log_oak_top.png` также нужно будет добавить в папку текстур в Behavior Pack, поскольку файл `terrain_texture.json`
настроен на поиск обеих текстур в папке `HelloWorldRP`.

1. Navigate to the `Vanilla_Resource_Pack\textures\blocks` folder and copy `log_oak_top.png`.
2. Navigate to `HelloWorldRP/textures/blocks` and paste a copy of `log_oak_top.png`.

## Настройка Behavior JSON-файла

После завершения работы в пакете ресурсов необходимо обновить пакет поведения, добавив в него компоненты блока `canvas`.

1. В **Проводнике** перейдите в папку `HelloWorldBP`, расположенную в папке `development_behavior_packs`.
2. Щелкните правой кнопкой мыши в окне `Проводника` и выберите `Создать`, затем выберите `Папку`.
3. Задайте имя - `blocks`.
4. Дважды щелкните на блоках, чтобы открыть папку.
5. Щелкните правой кнопкой мыши в окне `Проводника` и выберите `Создать`, затем выберите `Текстовый документ`.
6. Задайте имя `canvasblock.json`.
7. Дважды щелкните на файле `canvasblock.json`, чтобы открыть его в текстовом редакторе.

### Описание

В этом файле необходимо определить, что представляет собой блок, аналогично файлу `manifest.json`.

1. Скопируйте и вставьте следующий код:

``` json
{
    "format_version": "1.16.0",
    "minecraft:block": {
        "description": {
            "identifier": "helloworld:canvasblock",
            "is_experimental": false,
            "register_to_creative_menu": true
        },
```

Здесь определяется идентификатор, который использовался в ресурсном блоке. Блок также установлен для появления в
творческом меню и не установлен как экспериментальный фрагмент контента.

### Компоненты

1. В конце файла `CanvasBlock.json` (строка 9) скопируйте и вставьте следующий код:

``` json
        "components": {
            "minecraft:destroy_time": 1,
            "minecraft:explosion_resistance": 5,
            "minecraft:friction": 0.6,
            "minecraft:flammable": {
                "flame_odds": 0,
                "burn_odds": 0
            },
            "minecraft:map_color": "#FFFFFF",
            "minecraft:block_light_absorption": 0,
            "minecraft:block_light_emission": 0.250
        }
    }
}
```

2. Сохраните файл

+ `destroy_time` - сколько ударов игрока потребуется для уничтожения этого блока.
+ `explosion_resistance` - устойчивость блока к взрывам. Более высокие значения означают, что вероятность разрушения
  блока меньше.
+ `friction` используется для определения скорости игрока и существ при наступлении на этот блок. Дерево и грязь имеют
  трение 0,6, а лед - 0,1.
+ `flammable` используется для свойств того, как блок обрабатывает события пожара.
+ `flame_odds` - вероятность того, что блок загорится.
+ `burn_odds` - вероятность уничтожения блока при возгорании.
+ `map_color` - цвет в шестнадцатеричном формате, который используется картой для обозначения блока.
+ `block_light_absorption` - сколько света поглощает блок. Значение использует диапазон от 0 до 1 в качестве входных
  данных.
+ `block_light_emission` - сколько света производит блок. Значение использует диапазон от 0 до 1 в качестве входных
  данных.

## Установка имени блока с помощью .lang

Теперь, когда оба пакета установлены и завершены, осталось добавить имя блока с помощью `.lang`.

1. В **Проводнике** файлов перейдите в папку `HelloWorldRP`.
2. Щелкните правой кнопкой мыши в окне `Проводник` и выберите `Создать`, затем выберите `Папку`.
3. Задайте имя `texts`.
4. Дважды щелкните на `texts`, чтобы открыть папку.
5. Щелкните правой кнопкой мыши в окне `Проводник` и выберите `Создать`, затем выберите `Текстовый документ`.
6. Задайте имя `en_US.lang`
7. Дважды щелкните на `en_US.lang`, чтобы открыть его в текстовом редакторе.

### .lang

`.lang` - это тип файла, который Minecraft использует для предоставления внутриигрового текста на разных языках для
концепций в дополнениях. Файлы .lang также являются удобным способом организации всего пользовательского текста в аддоне
в одном месте, а также используются для локализации контента создателей.

1. Скопируйте и вставьте следующее в **en_US.lang**: `tile.helloworld:canvasblock.name=Canvas Block`
2. Сохраните и закройте.

В приведенном выше коде вы устанавливаете имя блока как `Canvas Block` в игре.

### Тестирование блока

Теперь, когда блок холста определен и в пакете поведения, и в пакете ресурсов, вы можете протестировать его в игре.

> Важно!
>
> Чтобы добавить блок в инвентарь, необходимо иметь мир Minecraft, в котором включены читы.
>
> Вам также потребуется включить оба пакета Hello World в мире, чтобы получить доступ к блоку холста.

+ Откройте диалоговое окно чата (T или Enter в ОС Windows 10).
+ Введите следующую команду: `/give @p helloworld:canvasblock`
