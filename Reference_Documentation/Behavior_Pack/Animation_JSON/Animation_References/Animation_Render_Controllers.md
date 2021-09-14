# Документация по анимации - Контроллеры рендеринга

Контроллеру рендеринга необходим идентификатор, который должен иметь формат "controller.render.<name>". Это имя должно
соответствовать имени, заданному в JSON определении клиентской сущности.

Контроллеры рендеринга - это способ для игрока определить, что будет рендериться на объекте. Игроки могут задавать
геометрию, материалы, текстуры и видимость частей сущности. Помимо непосредственной установки ключей, игроки могут
использовать массивы, чтобы заставить объект выбирать между различными вариантами.

## Начало работы

Для начала создайте новую папку с именем "render_controllers" в корне пакета ресурсов, в который вы хотите добавить
новый JSON контроллера рендеринга.

### Пример JSON контроллеров рендеринга для сущности оцелот

``` json
"format_version": "1.8.0",
"render_controllers": {
  "controller.render.ocelot": {
    //Декларации массивов
    "arrays": {
      //Декларации массивов текстур
      "textures": {
        //Имя свойства - идентификатор массива, за которым следует список ссылок на текстуры (см. entity/textures)
        "Array.skins": ["Texture.wild", "Texture.black", "Texture.red", "Texture.siamese"]
      }
    },
    //Указывает рендерингу использовать ссылки на геометрии (см. entity/geometries)
    "geometry": "Geometry.default",
    //Указывает рендерингу, какой материал использовать для каких костей, * используется для подстановочных знаков, используя ссылки на материалы (см. entity/material)
    "materials": [{ { "*": "Material.default" }],
    //Указывает рендеру, какие текстуры использовать на и в каком слое, используя ссылки на текстуры (см. entity/textures) или в данном случае ссылку на объявленный массив текстур
    "textures": ["Array.skins[query.variant]"]
  }
}
```

## Примеры

В следующих примерах вы увидите, как контроллеры рендеринга можно использовать для управления геометрией, материалами и
текстурами для различных сущностей. В каждом примере показан пример использования ванильной сущности.

### Пример массива для геометрии из JSON овцы

``` json
"arrays": {
  "geometries": {
    "Array.geos": ["Geometry.default", "Geometry.sheared"]
  }
},
"geometry": "Array.geos[query.is_sheared]",
```

### Пример массива для материалов из паука JSON

``` json
"arrays": {
  "materials": {
    "Array.materials": ["Material.default", "Material.invisible"]
  }
},
"materials": [{ "*": "Array.materials[query.is_invisible]" }],
```

### Пример массива для текстур от деревенского жителя JSON

``` json
"arrays": {
  "textures": {
    "Array.skins": ["Texture.farmer", "Texture.librarian", "Texture.priest", "Texture.smith", "Texture.butcher"]
  }
},
"textures": ["Array.skins[query.variant]"]
```

### Пример с цветом для подкрашивания частей из контроллера рендеринга Armor 1.0 JSON

``` json
"format_version": "1.8.0",
"render_controllers": {
    "controller.render.armor.chest.v1.0": {
        "arrays": {
            "materials": {
                "array.armor_material": [
                    "material.armor",
                    "material.armor_enchanted",
                    "material.armor_leather",
                    "material.armor_leather_enchanted"
                    ]
                },
            "textures": {
                "array.armor_texture": [
                    "texture.leather",
                    "texture.chain",
                    "texture.iron",
                    "texture.diamond",
                    "texture.gold"
                    ]
                }
            },
        "geometry": "geometry.armor",
        "materials" : [
            { "body": "array.armor_material[query.armor_material_slot(1)]" },
            { "leftarm": "array.armor_material[query.armor_material_slot(1)]" },
            { "rightarm": "array.armor_material[query.armor_material_slot(1)]" }
            ],
        "part_visibility" : [
            { "*": 0 },
            { "body": "query.has_armor_slot(1)" },
            { "leftarm": "query.has_armor_slot(1)" },
            { "rightarm": "query.has_armor_slot(1)" }
            ],
        "color": {
            "r": "query.armor_color_slot(1, 0)",
            "g": "query.armor_color_slot(1, 1)",
            "b": "query.armor_color_slot(1, 2)",
            "a": "query.armor_color_slot(1, 3)"
            },
        "textures": ["array.armor_texture[query.armor_texture_slot(1)]", "texture.enchanted"]
    }
}
```

### Пример с цветом is_hurt_color из контроллера рендеринга Creeper JSON

``` json
"format_version": "1.8.0",
"render_controllers": {
    "controller.render.creeper": {
    "geometry" : "Geometry.default",
    "materials" : [{ "*": "Material.default" }],
    "textures" : "Texture.default",
    "is_hurt_color" : {
        "r": 0.0,
        "g": 0.0,
        "b": 1.0,
        "a": 0.5,
    }
}
```

### Пример с цветом on_fire_color из контроллера рендеринга Fireball JSON

``` json
"format_version": "1.8.0",
"render_controllers": {
    "controller.render.fireball": {
    "geometry" : "Geometry.default",
    "materials" : [{ "*": "Material.default" }],
    "textures" : "Texture.default",
    "on_fire_color" : {
        "r": 0.0,
        "g": 0.0,
        "b": 0.0,
        "a": 0.0,
        }
    }
}
```

### Пример с цветом overlay_color из контроллера рендеринга Wither Boss JSON

``` json
"format_version": "1.8.0",
"render_controllers": {
    "controller.render.wither_boss": {
    "arrays": {
        "textures": {
            "Array.wither_state": ["Texture.invulnerable", "Texture.default"]
        }
    },
    "geometry" : "Geometry.default",
    "materials" : [{ "*": "Material.default" }],
    "textures" : ["Array.wither_state[variable.display_normal_skin]"],
    "overlay_color" : {
        "r": "variable.is_invulnerable ? 1.0 : this",
        "g": "variable.is_invulnerable ? 1.0 : this",
        "b": "variable.is_invulnerable ? 1.0 : this",
        "a": "variable.is_invulnerable ? query.overlay_alpha : this"
        }
    }
}
```

### Пример с part_visibility для включения и выключения видимости частей из Llama JSON

``` json
"format_version": "1.8.0",
"render_controllers": {
  "controller.render.llama": {
    "arrays": {
      "textures": {
        "Array.base": [
            "Texture.creamy",
            "Texture.white",
            "Texture.brown",
            "Texture.gray"
        ],
        "Array.decor": [
            "Texture.decor_none",
            "Texture.decor_white",
            "Texture.decor_orange",
            "Texture.decor_magenta",
            "Texture.decor_light_blue",
            "Texture.decor_yellow",
            "Texture.decor_lime",
            "Texture.decor_pink",
            "Texture.decor_gray",
            "Texture.decor_silver",
            "Texture.decor_cyan",
            "Texture.decor_purple",
            "Texture.decor_blue",
            "Texture.decor_brown",
            "Texture.decor_green",
            "Texture.decor_red",
            "Texture.decor_black"
            ]
        }
    },
    "geometry": "Geometry.default",
    "part_visibility": [{ "chest*": "query.is_chested" }],
    "materials": [{ "*": "Material.default" }],
    "textures": [
      "Array.base[query.variant]",
      "Array.decor[variable.decor_texture_index]",
      "Texture.decor_none"
    ]
  }
}
```

### Пример массива материалов из контроллеров рендеринга Horse

Седло будет переопределять гриву, которая будет переопределять TailA и т.д.

``` json
"materials": [
  { "*": "Material.default" },
  { "TailA": "Material.horse_hair" },
  { "Mane": "Material.horse_hair" },
  { "*Saddle*": "Material.horse_saddle" }
],
```
