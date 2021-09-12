# Создание вашего первого GameTest

## Что входит в GameTest?

GameTest - это миниатюрное окружение с набором начальных условий, например, набором мобов или предметов. После того как
это окружение немного поиграет в мире Minecraft, вы можете запустить условный код, чтобы оценить, оправдались ли ваши
ожидания.

Создание наборов GameTests требует создания GameTests с помощью пакета поведения и написания простого кода JavaScript.

> Важно!
>
> GameTest Framework все еще является экспериментальным. Как и все эксперименты, вы можете увидеть добавления, удаления и изменения в функциональности в версиях Minecraft без существенного предварительного предупреждения. Проверьте Minecraft Changelog для получения подробной информации о любых изменениях в GameTest Framework.

Поскольку GameTest Framework часто добавляет и обновляет функциональность, мы рекомендуем использовать последние
бета-версии Minecraft. Дополнительную информацию см. в разделе [Бета-версии Minecraft](https://aka.ms/mcbeta). Синтаксис
этого примера предназначен для совместимости с последними бета-версиями.

### Требования

Перед началом этого урока рекомендуется выполнить следующее.

+ [Введение в наборы параметров](../Adding_Content/Introduction_to_Behavior_Packs.md)

### Элементы GameTest

В рамках Behavior Pack каждый GameTest состоит из нескольких элементов:

**Структура**, определяющая физическую среду для испытания, а также любые начальные сущности. В Minecraft вы можете
создавать новые структуры, проектируя их (обычно в творческом режиме), а затем размещая рядом блок структуры. Затем вы
можете использовать блок структуры для сохранения результатов на диск. При этом создается файл .mcstructure, который
можно добавить к тесту.

При запуске GameTests в Minecraft ваша структура будет загружена и развернута в Minecraft. Следует отметить, что эта
структура будет создана и запущена в общем плоском, широком мире, поэтому вам нужно убедиться, что все мобы будут
вписаны в созданные вами структуры.

GameTests затем использует код JavaScript для определения теста, включая:

+ **Регистрация теста** - небольшое количество кода для создания теста в среде.
+ **Настройка теста** - дополнительный код, который устанавливает условия в созданной среде Structure. Как правило, это
  создание дополнительных мобов.
+ **Проверка теста** - дополнительные фрагменты кода, написанные на JavaScript, которые оценивают, успешно или неудачно
  завершился тест.

Благодаря этой простой основе, GameTests можно создать с помощью нескольких строк кода JavaScript и структуры Minecraft.

## Начните создавать свои тесты

Чтобы начать работу, вам нужно начать с собственного пакета поведения. Чтобы создать свой пакет поведения, создайте
новую папку в папке `development_behavior_packs` под названием `startertests`.

> Важно!
>
> Чтобы создавать и запускать собственные GameTests, вы должны использовать последние бета-версии Minecraft (версия 1.16.230+). Более подробную информацию смотрите в разделе [Бета-версии Minecraft](https://aka.ms/mcbeta).

В папку `startertests` необходимо включить две вложенные папки:

+ `structures` для хранения файлов MCStructure
+ `scripts` для хранения файлов JavaScript

### Обновите ваш манифест

Вы можете начать манифест пакета поведения с файла manifest.json в папке startertests следующим образом:

``` json
{
    "format_version": 2,
    "header": {
        "description": "Introductory tests for Minecraft GameTest Framework.",
        "name": "Starter Hello World Tests",
        "uuid": "1A2F42BD-98D4-4E0D-8E3F-934AB8A0C05E",
        "version": [0, 0, 1],
        "min_engine_version": [ 1, 14, 0 ]
    }
}
```

Манифест пакета поведения должен содержать дополнительные элементы для поддержки GameTests. В разделе `modules` должен
быть один модуль, добавленный под разделом header, который регистрирует точку входа вашего кода JavaScript, как показано
ниже:

``` json
"modules": [
        {
            "description": "Script that implements basic starter tests.",
            "type": "javascript",
            "uuid": "1A1B53FC-5653-4A75-91B7-9CDF027674AE",
            "version": [0, 0, 1],
            "entry": "scripts/StarterTests.js"
        }
    ]
```

Обратите внимание на несколько аспектов этого модуля:

+ Этот модуль имеет тип `javascript`.
+ UUID должен быть уникальным и сгенерированным для вашего проекта. Инструменты для генерации новых UUID см. в
  разделе [Введение в наборы параметров](../Adding_Content/Introduction_to_Behavior_Packs.md).
+ Атрибут `entry` указывает на файл JavaScript, содержащий ваш код GameTest.

Кроме того, вам необходимо установить зависимости от API Minecraft и GameTest Framework. Вы можете сделать это с помощью
дополнительных зависимостей, добавленных в разделе модулей ниже:

``` json
"dependencies": [
      {
        "uuid": "b26a4d4c-afdf-4690-88f8-931846312678",
        "version": [ 0, 1, 0 ]
      },
      {
        "uuid": "6f4b6893-1bb6-42fd-b458-7fa3d0c89616",
        "version": [ 0, 1, 0 ]
      }
    ]
```

> Предупреждение
>
> Обратите внимание, что здесь `uuid` относится к основным компонентам Minecraft. Вы **не** должны изменять эти значения в разделе зависимостей.

> Важно!
>
> Как вы можете видеть, тесты GameTest Framework зависят от версий "0.1.0" APIs Minecraft и GameTest Framework. Версия 0 означает, что эти функции все еще являются **экспериментальными**. Как и все эксперименты, мы улучшаем их возможности с течением времени, и сигнатуры API могут меняться от сборки к сборке без предварительного уведомления. Проверьте Minecraft Changelog, чтобы узнать больше изменений с течением времени.

Полный файл манифеста для Behavior Pack с GameTest выглядит следующим образом:

``` json
{
    "format_version": 2,
    "header": {
        "description": "Introductory tests for Minecraft GameTest Framework.",
        "name": "Starter Hello World Tests",
        "uuid": "1A2F42BD-98D4-4E0D-8E3F-934AB8A0C05E",
        "version": [0, 0, 1],
        "min_engine_version": [ 1, 14, 0 ]
    },
    "modules": [
        {
            "description": "Script that implements basic starter tests.",
            "type": "javascript",
            "uuid": "1A1B53FC-5653-4A75-91B7-9CDF027674AE",
            "version": [0, 0, 1],
            "entry": "scripts/StarterTests.js"
        }
    ],
    "dependencies": [
      {
        "uuid": "b26a4d4c-afdf-4690-88f8-931846312678",
        "version": [ 0, 1, 0 ]
      },
      {
        "uuid": "6f4b6893-1bb6-42fd-b458-7fa3d0c89616",
        "version": [ 0, 1, 0 ]
      }
    ]
}
```

### Регистрация GameTest

Каждый GameTest нуждается в файле сценария. Как вы видели в предыдущем разделе, мы добавили модуль с атрибутом `entry`,
который указывает на файл JavaScript:

``` json
"entry": "scripts/StarterTests.js"
```

Когда откроется мир с поддержкой GameTest Framework, в котором зарегистрирован этот файл, ваш файл GameTest JavaScript
будет загружен и выполнен. Здесь основная роль вашего кода заключается в регистрации последующих GameTest'ов.

Обратите внимание, что по мере внесения изменений в ваши скрипты или структуры, вам нужно будет выходить из вашего мира
и перезагружать его. Если есть какие-либо ошибки в сценарии, вы увидите их при загрузке мира.

Для регистрации скриптов GameTest вам понадобится класс RegistrationBuilder. Более подробную информацию о классе
Registration Builder можно найти на
странице [Registration Builder](https://docs.microsoft.com/ru-ru/minecraft/creator/scriptapi/mojang-gametest/registrationbuilder)

Пример строки JavaScript, использующей RegistrationBuilder, выглядит следующим образом:

``` js
// Registration Code for our test
GameTest.register("StarterTests", "simpleMobTest", simpleMobTest)
        .maxTicks(410)
        .structureName("startertests:mediumglass"); /* use the mediumglass.mcstructure file */

```

Эта строка кода создает новый тест под названием `simpleMobTest` в группе тестов `StarterTests`. Она добавляет
дополнительный параметр (`maxTicks`), который выражает, что этот тест может длиться 410 тиков (20,5 секунд). Наконец,
GameTest указывает MCStructure (`startertests:mediumglass`). По соглашению, это заставляет Minecraft использовать файл
MCStructure по адресу `/structures/startertests/mediumglass.mcstructure` в папке вашего Behavior Pack.

Остальная часть JavaScript использует класс GameTest Helper, чтобы фактически выразить тест в функции `simpleMobTest`.

### Функции тестирования

Тестовые функции - это место, где происходит фактическое выполнение теста. Функция тестирования задает начальные условия
для выполнения теста и возвращает дополнительную функцию тестирования, в которой оцениваются критерии.

Образец теста:

``` js
import * as GameTest from "mojang-gametest";
import { BlockLocation } from "mojang-minecraft";

function simpleMobTest(test) {
  const attackerId = "fox";
  const victimId = "chicken";

  test.spawn(attackerId, new BlockLocation(5, 2, 5));
  test.spawn(victimId, new BlockLocation(2, 2, 2));

  test.assertEntityPresentInArea(victimId, true);

  // Succeed when the victim dies
  test.succeedWhen(() => {
    test.assertEntityPresentInArea(victimId, false);
  });
};
```

Некоторые вещи, на которые следует обратить внимание в этой тестовой функции:

+ Вы можете использовать метод `spawn` для создания новых мобов в вашем тесте.
+ Координаты, используемые в API, такие, как spawn, являются относительными в пределах вашей .MCStructure.
+ Функции `assert` заставляют выполнение кода останавливаться, если условия, описанные в методе, не являются истинными.
  Здесь код утверждает, что курицы больше нет в структуре (`false` в методе assertEntityPresentInArea указывает функции
  утверждать, что сущности больше нет). Если в любом из блоков структуры будет найдена одна сущность, код `assert`
  выдаст ошибку. Однако если сущность не найдена, мы переходим к строке кода test.succeed, и тест проходит.

Полный файл JavaScript StarterTests.js выглядит следующим образом:

``` js
import * as GameTest from "mojang-gametest";
import { BlockLocation } from "mojang-minecraft";

function simpleMobTest(test) {
  const attackerId = "fox";
  const victimId = "chicken";

  test.spawn(attackerId, new BlockLocation(5, 2, 5));
  test.spawn(victimId, new BlockLocation(2, 2, 2));

  test.assertEntityPresentInArea(victimId, true);

  // Succeed when the victim dies
  test.succeedWhen(() => {
    test.assertEntityPresentInArea(victimId, false);
  });
};

// Registration Code for our test
GameTest.register("StarterTests", "simpleMobTest", simpleMobTest)
        .maxTicks(410)
        .structureName("startertests:mediumglass"); /* use the mediumglass.mcstructure file */
```

Чтобы завершить образец, вы захотите использовать блок структуры для определения теста.

Для этого откройте Minecraft и начните новый мир в режиме Creative, чтобы построить окружение. Это простая стеклянная
ручка, которая была построена для нашего GameTest, из стеклянных блоков:

![glasspen.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/gametestbuildyourfirstgametest/glasspen.png)

Затем вам нужно экспортировать это как структуру. Выполните следующую команду в Minecraft:

`/give @s structure_block`.

Это даст вам блок структуры для работы. Поместите Структурный блок рядом с вашим творением и используйте всплывающее
окно для обрамления вашего творения. Экспортируйте его как `mediumglass.mcstructure`.

![structureblock.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/gametestbuildyourfirstgametest/structureblock.png)

В пакете поведения перейдите в папку structures и создайте подпапку startertests.

Поместите этот файл mediumglass.mcstructure в подпапку с названием startertests. Убедитесь в том, что вы соблюдаете
регистр, указанный в коде JavaScript, поэтому сделайте его полностью строчным. Скопируйте файл mediumglass.mcstructure в
эту папку. Ваша папка должна выглядеть следующим образом:

![startertestfolder.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/gametestbuildyourfirstgametest/startertestfolder.png)

## Запуск тестов в игре

После того как вы завершили создание пакета поведения GameTest, вы захотите опробовать его в Minecraft. Для этого
создайте новый мир Minecraft. Для этого нового мира запустите режим Creative и включите эксперимент GameTest Framework.
Добавьте в свой мир поведенческие пакеты GameTeset Behavior Packs. Если все сделано правильно, то при создании мира вы
должны увидеть Behavior Pack Start Hello World GameTest:

![behaviorpack.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/gametestbuildyourfirstgametest/behaviorpack.png)

Нажмите на плитку Behavior Pack Starter Hello World, чтобы активировать ее.

> Важно!
>
> Вы также, вероятно, захотите указать некоторые дополнительные изменения в вашей среде:
>
> * Выберите плоский мир
> * Сохраните нормальную сложность (мобы работают по-другому в полностью мирных мирах)

После загрузки мира используйте команду `/gametest для запуска тестов`.

Чтобы запустить конкретный тест, используйте команду `/gametest run <classname>:<testName>`, например:

`/gametest run startertests:simpleMobTest`

## Что дальше?

Вы создали свой первый тест GameTest Framework. Тесты GameTest позволяют вам, как создателю, растягивать контент,
упражнять сущности и проверять механику геймплея. Вы можете просмотреть API GameTest ниже, чтобы узнать больше о том,
что входит в GameTest Framework.

[API GameTest](../../Reference_Documentation/GameTest/GameTest_API/Modules/mojang-gametest/mojang-gametest.md)
