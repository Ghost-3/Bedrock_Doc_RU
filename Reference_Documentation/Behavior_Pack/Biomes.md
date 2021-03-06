# Документация по биомам - Обзор

Биомы описывают, как должен выглядеть и вести себя локальный участок мира. Написав пользовательские данные о биомах, вы можете:

+ Изменить общую форму местности для биома.
+ Изменить соотношение частоты встречаемости типов биомов.
+ Изменить блоки, из которых состоит биом, как на поверхности, так и под ней.
+ Изменить распределение декоративных элементов (например, деревьев, травы и т.д.) для биома.
+ Изменить порождаемых мобов для биома.
+ Изменить климат для биома.

## Формат JSON

Все биомы должны указать версию, на которую они ориентированы, через поле `format_version`. Остальные данные биома разделены на независимые JSON-субъекты, или компоненты. В общем случае можно считать, что наличие компонента определяет, в каком игровом поведении участвует биом, а поля компонента определяют, как он участвует. В целом существует две категории компонентов:

1. Компоненты с пространством имен (т.е. компоненты с префиксом `name`:) связываются с определенным поведением в игре; они могут иметь поля-члены, которые параметризуют это поведение; поддерживаются только имена, имеющие корректное сопоставление.
2. Компоненты без пространства имен рассматриваются как "теги": допускается любое имя, состоящее из буквенно-цифровых символов, '.' и '_'; тег прикрепляется к биому, чтобы код или данные могли проверить его существование; компоненты тегов не могут иметь полей-членов.

Дополнительные подробности и полный список компонентов с именами см. в полной схеме биома ниже.

### Пример

``` json
{
  "plains": {
    "format_version": "1.12.0",

    "minecraft:climate": {
      "downfall": 0.4,
      "snow_accumulation": [ 0.0, 0.125 ],
      "temperature": 0.8
    },
    "minecraft:overworld_height": {
      "noise_type": "lowlands"
    },
    "minecraft:surface_parameters": {
      "sea_floor_depth": 7,
      "sea_floor_material": "minecraft:gravel",
      "foundation_material": "minecraft:stone",
      "mid_material": "minecraft:dirt",
      "top_material": "minecraft:grass"
    },
    "minecraft:overworld_generation_rules": {
      "hills_transformation": [
        [ "forest_hills", 1 ],
        [ "forest", 2 ]
      ],
      "mutate_transformation": "sunflower_plains",
      "generate_for_climates": [
        [ "medium", 3 ],
        [ "warm", 1 ],
        [ "cold", 1 ]
      ]
    },

    "animal": {},
    "monster": {},
    "overworld": {},
    "plains": {}
  }
}
```

## Добавление новых биомов

Биомы считываются из файлов JSON в подпапках biomes поведенческих пакетов. При загрузке используется один биом на файл; имя файла и фактическое имя биома должны совпадать. Добавление файла с новым именем в местоположение данных биома сделает его доступным для использования игрой, в то время как существующие биомы могут быть перезаписаны с помощью файлов, совпадающих с их существующим именем.

> Важно!
> 
> Если вы добавляете новый биом, вам необходимо записать данные компонента, позволяющие ему участвовать в генерации мира (см. полную схему ниже), иначе он не появится в ваших мирах.

---

> Совет
> 
> Примеры кода ниже помечены языком программирования C, чтобы иметь схожую с Molang подсветку синтаксиса и используемую схему.

### Схема

``` json
{
    object "minecraft:climate"[0,7] : opt // Описывает температуру, влажность, осадки и т.д.  Биомы без этого компонента будут иметь значения по умолчанию.
    {
        float "temperature" : opt
        float "downfall" : opt
        float "red_spores" : opt
        float "blue_spores" : opt
        float "ash" : opt
        float "white_ash" : opt
        array "snow_accumulation"[2] : opt
        {
            float "[0..0]"
            float "[1..1]"
        }
    }
    object "minecraft:overworld_height"[0,2] : opt // Параметры шума, используемые для управления высотой рельефа в Верхнем мире.
    {
        array "noise_params"[2] : opt
        {
            float "[0..0]"
            float "[1..1]"
        }
        string "noise_type"<"stone_beach", "deep_ocean", "default", "default_mutated", "lowlands", "river", "ocean", "taiga", "mountains", "highlands", "mushroom", "less_extreme", "extreme", "beach", "swamp"> : opt
    }
    object "minecraft:forced_features"[0,1] : opt // Заставить определенные декоративные элементы (деревья, растения и т.д.) появиться в этом биоме, независимо от обычных правил декорирования.
    {
        array "<identifier>" : opt
        {
            object "<any array element>" : opt
            {
                molang "iterations" // Количество разбросанных позиций для генерации
                object "scatter_chance" : opt // Числитель / знаменатель вероятности того, что данный разброс произойдет.  Не оценивается на каждой итерации; либо не будет выполнено ни одной итерации, либо будут выполнены все.
                {
                    int "numerator"<1-*>
                    int "denominator"<1-*>
                }
                molang "scatter_chance" : opt // Вероятность (0-100) того, что данный разброс произойдет.  Не оценивается на каждой итерации; либо не будет выполнено ни одной итерации, либо будут выполнены все.
                enumerated_value "coordinate_eval_order"<"xyz", "xzy", "yxz", "yzx", "zxy", "zyx"> : opt // Порядок, в котором будут оцениваться координаты. Следует использовать, когда одна координата зависит от другой. If omitted, defaults to "xzy".
                molang "x" : opt // Выражение для координаты (оценивается на каждой итерации).  Взаимоисключающий с объектом случайного распределения below.
                object "x" : opt // Распределение для координаты (оценивается на каждой итерации).  Взаимоисключающее с выражением Molang выше.
                {
                    enumerated_value "distribution"<"uniform", "gaussian", "inverse_gaussian", "fixed_grid", "jittered_grid"> // Тип распределения - равномерное случайное, гауссово (с центром в диапазоне), или сетка (с фиксированным шагом или прерывистое).
                    int "step_size"<1-*> : opt // Если тип распределения - сетка, определяет расстояние между шагами вдоль этой оси
                    int "grid_offset"<0-*> : opt // Когда тип распределения - сетка, определяет смещение вдоль этой оси
                    array "extent"[2]
                    {
                        molang "[0..0]" : opt // Нижняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса по окружности
                        molang "[1..1]" : opt // Верхняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса вокруг
                    }
                }
                molang "z" : opt // Выражение для координаты (оценивается на каждой итерации).  Взаимоисключающий с объектом случайного распределения ниже.
                object "z" : opt // Распределение для координаты (оценивается на каждой итерации).  Взаимоисключающее с выражением Molang выше.
                {
                    enumerated_value "distribution"<"uniform", "gaussian", "inverse_gaussian", "fixed_grid", "jittered_grid"> // Тип распределения - равномерное случайное, гауссово (с центром в диапазоне), или сетка (с фиксированным шагом или прерывистое).
                    int "step_size"<1-*> : opt // Если тип распределения - сетка, определяет расстояние между шагами along this axis
                    int "grid_offset"<0-*> : opt // Если тип распределения - сетка, определяет смещение вдоль этой оси
                    array "extent"[2]
                    {
                        molang "[0..0]" : opt // Нижняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса по окружности
                        molang "[1..1]" : opt // Верхняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса вокруг
                    }
                }
                molang "y" : opt // Выражение для координаты (оценивается на каждой итерации).  Взаимоисключающий с объектом случайного распределения ниже.
                object "y" : opt // Распределение для координаты (оценивается на каждой итерации).  Взаимоисключающее с выражением Molang выше.
                {
                    enumerated_value "distribution"<"uniform", "gaussian", "inverse_gaussian", "fixed_grid", "jittered_grid"> // Тип распределения - равномерное случайное, гауссово (с центром в диапазоне), или сетка (с фиксированным шагом или прерывистое).
                    int "step_size"<1-*> : opt   // Если тип распределения - сетка, определяет расстояние между шагами вдоль этой оси
                    int "grid_offset"<0-*> : opt // Когда тип распределения - сетка, определяет смещение вдоль этой оси
                    array "extent"[2]
                    {
                        molang "[0..0]" : opt // Нижняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса по окружности
                        molang "[1..1]" : opt // Верхняя граница (включительно) диапазона разброса, как смещение от точки входа до разброса вокруг
                    }
                }
                feature_reference "places_feature"
                string "identifier"
            }
        }
    }
    object "minecraft:ignore_automatic_features" : opt // Никакие особенности не будут автоматически прикреплены к этому биому, появятся только особенности, указанные в компоненте minecraft:forced_features.
    object "minecraft:surface_parameters"[0,6] : opt // Управление блоками, используемыми для генерации рельефа по умолчанию в Верхнем мире Minecraft.
    {
         "top_material" // Управляет типом блока, используемого для поверхности этого биома.
         "mid_material" // Управляет типом блока, используемого в слое под поверхностью этого биома.
         "sea_floor_material" // Управляет типом блока, используемого в качестве дна для водоемов в этом биоме.
         "foundation_material" // Управляет типом блока, используемого глубоко под землей в этом биоме.
         "sea_material" // Управляет типом блока, используемого для водоемов в этом биоме.
        int "sea_floor_depth" // Управляет глубиной залегания дна ниже уровня мировой воды.
    }
    object "minecraft:surface_material_adjustments"[0,1] : opt // Задать тонкие изменения блоков, используемых при генерации рельефа (на основе функции шума)
    {
        array "adjustments" : opt // Все корректировки, соответствующие значениям шума в колонке, будут применены в указанном порядке.
        {
            object "<any array element>"
            {
                object "materials"
                {
                     "top_material" : opt // Управляет типом блока, используемого для поверхности этого биома, когда активна эта корректировка.
                     "mid_material" : opt // Управляет типом блока, используемого в слое под поверхностью этого биома, когда эта настройка активна.
                     "sea_floor_material" : opt // Управляет типом блока, используемого в качестве дна для водоемов в этом биоме, когда эта настройка активна.
                     "foundation_material" : opt // Управляет типом блока, используемого глубоко под землей в этом биоме, когда эта настройка активна.
                     "sea_material" : opt // Управляет типом блока, используемого в водоемах в этом биоме, когда эта настройка активна.
                }
                array "noise_range"[2] : opt // Определяет диапазон значений шума [min, max], для которых должна применяться эта регулировка.
                {
                    float "[0..0]"<-1.000000-1.000000>
                    float "[1..1]"<-1.000000-1.000000>
                }
                array "height_range"[2] : opt // Определяет диапазон значений шума [min, max], для которых должна применяться эта регулировка.
                {
                    molang "[0..0]"
                    molang "[1..1]"
                }
                float "noise_frequency_scale" : opt // Масштаб для умножения на позицию при получении значения шума для регулировки материала.
            }
        }
    }
    object "minecraft:swamp_surface"[0,6] : opt // Аналогично overworld_surface. Добавляет детали поверхности болота.
    {
         "top_material" // Управляет типом блока, используемого для поверхности этого биома.
         "mid_material" // Управляет типом блока, используемого в слое под поверхностью этого биомаme.
         "sea_floor_material" // Управляет типом блока, используемого в качестве дна для водоемов в этом биоме.iome.
         "foundation_material" // Управляет типом блока, используемого глубоко под землей в этом биоме.
         "sea_material" // Управляет типом блока, используемого для водоемов в этом биоме.
        int "sea_floor_depth" // Управляет глубиной залегания дна ниже уровня мировой воды.
    }
    object "minecraft:frozen_ocean_surface"[0,6] : opt // Аналогично overworld_surface. Добавляет айсберги.
    {
         "top_material" // Управляет типом блока, используемого для поверхности этого биома.
         "mid_material" // Управляет типом блока, используемого в слое под поверхностью этого биома.
         "sea_floor_material" // Управляет типом блока, используемого в качестве дна для водоемов в этом биоме.
         "foundation_material" // Управляет типом блока, используемого глубоко под землей в этом биоме.
         "sea_material" // Управляет типом блока, используемого для водоемов в этом биоме.
        int "sea_floor_depth" // Управляет глубиной залегания дна ниже уровня мировой воды.
    }
    object "minecraft:mesa_surface"[0,10] : opt // Аналогичен overworld_surface.  Добавляет цветные пласты и необязательные столбы.
    {
         "top_material" // Управляет типом блока, используемого для поверхности этого биома.
         "mid_material" // Управляет типом блока, используемого в слое под поверхностью этого биома.
         "sea_floor_material" // Управляет типом блока, используемого в качестве дна для водоемов в этом биоме.
         "foundation_material" // Управляет типом блока, используемого глубоко под землей в этом биоме.
         "sea_material" // Управляет типом блока, используемого для водоемов в этом биоме.
        int "sea_floor_depth" // Управляет глубиной залегания дна ниже уровня мировой воды.
         "clay_material"
         "hard_clay_material"
        bool "bryce_pillars"
        bool "has_forest"
    }
    object "minecraft:nether_surface" : opt // Используйте стандартную генерацию местности Нижнего мира Minecraft.
    object "minecraft:the_end_surface" : opt // Используйте стандартную генерацию рельефа Края Minecraft.
    object "minecraft:capped_surface"[0,5] : opt // Генерирует поверхность на блоках с нетвердыми блоками выше или ниже.
    {
        array "floor_materials"[1,*] // Материалы, используемые для покрытия пола.
        {
            block_reference "<any array element>"
        }
        array "ceiling_materials"[1,*] // Материалы, используемые для потолка поверхности.
        {
            block_reference "<any array element>"
        }
        block_reference "sea_material" // Материал, используемый для замены воздушных блоков ниже уровня моря.
        block_reference "foundation_material" // Материал, используемый для восстановления твердых блоков, которые не являются поверхностными блоками.
        block_reference "beach_material" : opt // Материал, используемый для декорирования поверхности вблизи уровня моря.
    }
    object "minecraft:mountain_parameters"[0,3] : opt // Параметры шума, используемые для генерации горного рельефа в Верхнем мире
    {
        float "peaks_factor" : opt
        object "steep_material_adjustment" : opt // Определяет материал поверхности для крутых склонов
        {
             "material" : opt // Использование блоков в качестве материала для откосов.
            bool "north_slopes" : opt // Разрешить для склонов, обращенных на север
            bool "south_slopes" : opt // Разрешить для склонов, обращенных на юг
            bool "west_slopes" : opt // Разрешить для западных склонов
            bool "east_slopes" : opt // Разрешено для восточных склонов
        }
        object "top_slide" : opt // Управляет сужением плотности, которое происходит в верхней части мира, чтобы предотвратить слишком высокий рельеф местности
        {
            bool "enabled" // Если false, верхний слой будет отключен. Если true, будут учитываться другие параметры
        }
    }
    object "minecraft:overworld_generation_rules"[0,5] : opt // Контролирует, как этот биом будет создан (и затем потенциально изменен) во время генерации Верхнего мира.
    {
        biome_reference "hills_transformation" : opt
        array "hills_transformation"[1,*] : opt
        {
            biome_reference "<any array element>" : opt
            array "<any array element>"[2] : opt
            {
                biome_reference "[0..0]"
                int "[1..1]"
            }
        }
        biome_reference "mutate_transformation" : opt
        array "mutate_transformation"[1,*] : opt
        {
            biome_reference "<any array element>" : opt
            array "<any array element>"[2] : opt
            {
                biome_reference "[0..0]"
                int "[1..1]"
            }
        }
        array "generate_for_climates" : opt // Управляет климатическими категориями генерации мира, для которых этот биом может порождать.  Один биом может быть связан с несколькими категориями с разным весом.
        {
            array "<any array element>"[2]
            {
                enumerated_value "[0..0]"<"medium", "warm", "lukewarm", "cold", "frozen"> // Название категории климата
                int "[1..1]" // Вес, с которым этот биом должен быть выбран, по отношению к другим биомам в той же категории
            }
        }
        biome_reference "river_transformation" : opt
        array "river_transformation"[1,*] : opt
        {
            biome_reference "<any array element>" : opt
            array "<any array element>"[2] : opt
            {
                biome_reference "[0..0]"
                int "[1..1]"
            }
        }
        biome_reference "shore_transformation" : opt
        array "shore_transformation"[1,*] : opt
        {
            biome_reference "<any array element>" : opt
            array "<any array element>"[2] : opt
            {
                biome_reference "[0..0]"
                int "[1..1]"
            }
        }
    }
    object "minecraft:multinoise_generation_rules"[0,5] : opt // Управляет тем, как этот биом будет создан (и затем потенциально изменен) во время генерации Нижнего мира.
    {
        float "target_temperature" : opt // Температура, с которой должен быть выбран этот биом, относительно других биомов.
        float "target_humidity" : opt // Влажность, с которой этот биом должен быть выбран, относительно других биомов.
        float "target_altitude" : opt // Высота, с которой этот биом должен быть выбран, относительно других биомов.
        float "target_weirdness" : opt // Странность, с которой этот биом должен быть выбран, относительно других биомов.
        float "weight" : opt // Вес, с которым этот биом должен быть выбран, относительно других биомов.
    }
    object "minecraft:legacy_world_generation_rules" : opt // Дополнительный контроль генерации миров, применимый только к ограниченным мирам наследия.
    object "[a-z0-9_.:]+" : opt // Прикрепите произвольные строковые метки к этому биому
}
```
