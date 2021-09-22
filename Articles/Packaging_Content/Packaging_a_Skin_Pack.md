# Упаковка пакета скинов

В этом руководстве вы узнаете следующее:

+ Структура папок и файлов для скин-паков в Minecraft: Bedrock Edition.
+ Как создать необходимые файлы метаданных для скин-пака и как определить скин с их помощью.

### Структура папок скин-пака

![folderstructure.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/packagingaskinpack/folderstructure.png)

## manifest.json

Манифест сообщает Minecraft общую информацию о вашем скин-пакете. Создайте JSON-файл с именем `manifest.json` в корне
скин-пака. В нем содержится следующее:

+ `name`: имя пакета, которое всегда равно `pack.name`.
+ `version`: версия пакета. Например, `[1, 0 ,0]` означает версию 1.0.0.
+ `uuid`: уникальный идентификатор для предотвращения конфликтов пакетов, который можно сгенерировать на этом
  сайте: <https://www.uuidgenerator.net/version4> **(необходимо сгенерировать два разных UUID)**.
+ `type`: установите значение `skin_pack`, чтобы указать игре рассматривать этот пакет как пакет скинов.

### Шаблон manifest.json

``` json
{
  "header": {
    "name": "pack.name",
    "version": [1, 0, 0],
    "uuid": "<ПЕРВЫЙ СГЕНЕРИРОВАННЫЙ UUID>"
  },
  "modules": [
    {
      "version": [1, 0, 0],
      "type": "skin_pack",
      "uuid": "<ВТОРОЙ СГЕНЕРИРОВАННЫЙ UUID>"
    }
  ],
  "format_version": 1
}
```

## skins.json

Файл `skins.json` определяет скины, которые поставляются с вашим скин-паком. Создайте JSON-файл с именем `skins.json` в
корне скин-пакета. Внутри него содержится следующее:

+ `localization_name` и `serialize_name`: они будут одинаковыми и являются ключами локализации, значение которых будет
  определено позже в [en_US.lang](#en_uslang) с полным ключом `skinpack.<localization_name>`. Это значение будет
  названием пакета. Этот ключ также всегда будет добавляться к ключу локализации каждого отдельного скина.
+ `skins`: набор определений, каждое из которых определяет один скин.

Каждое отдельное определение скина будет содержать следующее:

+ `localization_name`: ключ локализации, значение которого определяется позже в `en_US.lang`. Значение будет именем
  индивидуального скина.
+ `geometry`: базовая модель, для которой предназначен данный скин. `geometry.humanoid.customSlim` - модель
  Alex, `geometry.humanoid.custom` - модель Steve.
+ `texture`: имя файла для каждой из текстур скина, как они отображаются в корне пакета скинов.
+ `type`: либо `free`, либо `paid`. Партнеры, не являющиеся участниками рынка, могут иметь любое количество бесплатных
  скинов, но не платных, в то время как участники рынка могут иметь до 2 бесплатных скинов и могут добавлять платные
  скины.

### Шаблон skins.json

``` json
{
  "serialize_name": "TemplateSkinPack",
  "localization_name": "TemplateSkinPack",
  "skins": [
    {
      "localization_name": "TemplateSkin1",
      "geometry": "geometry.humanoid.customSlim",
      "texture": "skin_file_name1.png",
      "type": "free"
    },
    {
      "localization_name": "TemplateSkin2",
      "geometry": "geometry.humanoid.custom",
      "texture": "skin_file_name2.png",
      "type": "free"
    },
    {
      "localization_name": "TemplateSkin3",
      "geometry": "geometry.humanoid.customSlim",
      "texture": "skin_file_name3.png",
      "type": "paid"
    },
    {
      "localization_name": "TemplateSkin4",
      "geometry": "geometry.humanoid.custom",
      "texture": "skin_file_name4.png",
      "type": "paid"
    },
    {
      "localization_name": "TemplateSkin5",
      "geometry": "geometry.humanoid.custom",
      "texture": "skin_file_name5.png",
      "type": "paid"
    }
  ]
}
```

## Текстуры скинов

Фактические текстуры скинов представляют собой PNG-файлы. Имена файлов указаны в файле метаданных skins.json. Они могут
использоваться только в корне пакета скинов. Вы можете использовать [Blockbench](https://blockbench.net/) для создания
пригодного для использования PNG для вашего скин-пака.

## Папка Texts

В этой папке находятся файлы `en_US.lang` и `languages.json`, которые определяют фактические названия вашего пакета и
скинов, а также поддерживаемые языки вашего пакета. Имена после `=` - это то, что отображается в игре, например, в окне
выбора скина.

### en_US.lang

Это файл, в котором вы даете имя своему пакету и скинам.

    Имя пакета: `skinpack.[skins.json localization_name]=[имя пакета]`.
    Имя скина: `skin.[skins.json localization_name].[skins.json single skin localization_name]=[имя скина]`.

Приведенный ниже шаблон использует "ключи локализации" из шаблона `skin.json` для названия пакета "Your Skin Pack Name Here" и для названия отдельных скинов "Skin Name 1-5".

#### Шаблон en_US.lang

```
skinpack.TemplateSkinPack=Your Skin Pack Name Here
skin.TemplateSkinPack.TemplateSkin1=Skin Name 1
skin.TemplateSkinPack.TemplateSkin2=Skin Name 2
skin.TemplateSkinPack.TemplateSkin3=Skin Name 3
skin.TemplateSkinPack.TemplateSkin4=Skin Name 4
skin.TemplateSkinPack.TemplateSkin5=Skin Name 5
```

#### Шаблон ru_RU.lang

```
skinpack.TemplateSkinPack=Ваше Название Скин-Пака Здесь
skin.TemplateSkinPack.TemplateSkin1=Название Скина 1
skin.TemplateSkinPack.TemplateSkin2=Название Скина 2
skin.TemplateSkinPack.TemplateSkin3=Название Скина 3
skin.TemplateSkinPack.TemplateSkin4=Название Скина 4
skin.TemplateSkinPack.TemplateSkin5=Название Скина 5
```

### languages.json

Этот файл сообщает Minecraft, какие языки поддерживает ваш скин-пак. Требуется только английский язык. Если вы хотите поддерживать другие языки, вы можете создать другие файлы xx_YY.lang, а затем отредактировать этот, чтобы сообщить игре, что вы их поддерживаете.

В настоящее время поддерживаются следующие локали/языки:

+ "en_US"
+ "de_DE"
+ "ru_RU"
+ "zh_CN"
+ "fr_FR"
+ "it_IT"
+ "pt_BR"
+ "fr_CA"
+ "zh_TW"
+ "es_MX"
+ "es_ES"
+ "pt_PT"
+ "en_GB"
+ "ko_KR"
+ "ja_JP"
+ "nl_NL"
+ "bg_BG"
+ "cs_CZ"
+ "da_DK"
+ "el_GR"
+ "fi_FI"
+ "hu_HU"
+ "id_ID"
+ "nb_NO"
+ "pl_PL"
+ "sk_SK"
+ "sv_SE"
+ "tr_TR"
+ "uk_UA"

#### Шаблон languages.json

``` json
[
  "en_US",
  "ru_RU"
]
```
