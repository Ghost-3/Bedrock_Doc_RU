# Использование инструментов Visual Studio Code для написания скриптов

Два новых инструмента могут сделать процесс написания скриптов GameTest в Visual Studio Code проще и интереснее.

## Файл пользовательских типов для Intellisense в Visual Studio Code

Visual Studio Code может воспользоваться библиотеками подробной информации о типах для различных библиотек для
предоставления подсказок и выпадающих окон по мере ввода. Для модулей GameTest - `mojang-minecraft` и `mojang-gametest`

- доступны два новых модуля, позволяющие воспользоваться этим преимуществом.

Чтобы начать работу, используйте менеджер пакетов Node, или npm. npm позволяет легко загружать и устанавливать различные
модули кода в ваши пакеты. Установите Node.js - который включает npm - на ваше устройство разработки. Более подробную
информацию об установке npm можно найти на сайте https://nodejs.org. Установите последнюю LTS-версию Node.js, чтобы
начать работу.

После установки node.js получить последние определения типов будет проще простого. В папке проекта, в которой вы обычно
редактируете свои пакеты параметров, просто выполните следующие команды из командной строки:

``` PowerShell
npm i @types/mojang-minecraft
npm i @types/mojang-gametest
```

Это установит определения типов в папку node_modules вашего проекта.

Для редактирования с новыми подсказками кода просто откройте Visual Studio Code. Когда вы пишете JavaScript, вы должны
увидеть автозаполнение:

![autocomplete.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/autocomplete.png)

и встроенную справочную документацию по типам:

![inlinedocumentation.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/inlinedocumentation.png)

> Примечание
>
> Мы обновляем эти определения типов в соответствии с последними бета-версиями API, поэтому не забудьте часто проверять npm на наличие обновленных определений типов.

## Получите представление о своем коде с помощью отладки скриптов Minecraft

По мере того, как вы будете создавать все больше кодовой базы на скриптах, вы захотите проверять свой код в различных
точках, чтобы увидеть состояние переменных и протестировать свои алгоритмы. Во многих стартовых проектах люди начинают с
использования таких команд, как Console.log или Chat, чтобы выводить различные переменные по ходу работы - неофициально
это называется "отладка печати". Но для разработчиков есть лучший способ! С помощью скриптов в GameTest в Minecraft
Bedrock Edition вы можете использовать возможности отладки скриптов, которые делают проверку данных в скрипте Minecraft
простым делом.

Чтобы начать, вам нужно использовать Visual Studio Code в качестве редактора для файлов JavaScript, которые вы
разрабатываете. Далее следуют следующие шаги:

1. Установите отладчик Minecraft Bedrock Edition в Visual Studio Code - вам нужно будет сделать это один раз.
2. Откройте Visual Studio Code в папке development_behavior_packs.
3. В зависимости от вашего клиента тестирования - либо в Bedrock Dedicated Server, либо в клиентах Minecraft Bedrock -
   соедините Minecraft Bedrock Edition и Visual Studio Code.
4. Установите точки останова и добавьте переменные наблюдения в ваш код по ходу дела, а затем подключите Minecraft к
   Visual Studio Code

### Отладка в Minecraft Bedrock Edition

#### Шаг 1: Установите отладчик Minecraft Bedrock Edition в Visual Studio Code

Чтобы использовать возможности отладчика, вам необходимо установить отладчик Minecraft Bedrock Edition Debugger в Visual
Studio Code. Для этого нажмите на кнопку ниже, чтобы загрузить отладчик **Minecraft Bedrock Edition Debugger** из
магазина Visual Studio Code.

[Minecraft Bedrock Edition Debugger](https://aka.ms/vscodescriptdebugger)

#### Шаг 2: Убедитесь, что клиент Minecraft Bedrock Edition может делать запросы "loopback".

Если вы хотите подключить клиент Minecraft Bedrock Edition к Visual Studio Code, запущенному на той же машине (это
наиболее распространенный сценарий), вам нужно освободить клиент Minecraft от ограничений UWP loopback. Для этого
выполните следующие действия из командной строки или приложения Start | Run.

``` PowerShell
CheckNetIsolation.exe LoopbackExempt –a –p=S-1-15-2-1958404141-86561845-1752920682-3514627264-368642714-62675701-733520436
```

![commandprompt.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/commandprompt.png)

#### Шаг 3: Откройте Visual Studio Code в папке development_behavior_packs.

Для того чтобы отладчик знал, где найти ваши исходные файлы JavaScript, вам нужно будет открыть окно Visual Studio Code
относительно пакета параметров, в котором находятся ваши исходные файлы JavaScript.

Во время создания геймтестов вы, скорее всего, развернете их в папку development_behavior_packs в Minecraft. Она
находится в папке:

`%localappdata%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang\development_behavior_packs`

Выберите пакет параметров, который вы хотите отлаживать, и откройте окно Visual Studio Code, указав на эту папку.

#### Шаг 4: Подготовьте Visual Studio Code к подключению

Для отладки в Minecraft Bedrock Edition вам нужно будет подключиться из Minecraft к Visual Studio Code. Этот пример
предполагает, что вы отлаживаете на одной машине с Windows 10, но вы также можете отлаживать на разных машинах и
клиентах, если хотите. Если вы отлаживаете на разных устройствах, вам может понадобиться открыть порт в брандмауэре на
машине, на которой вы запускаете Visual Studio Code.

Чтобы настроить соединение, добавьте подпапку .vscode в папку вашего пакета параметров. В папку .vscode добавьте
следующий файл конфигурации launch.json:

(ПРИМЕЧАНИЕ: вам не нужно редактировать никакие строки этого файла).

``` json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "minecraft-js",
      "request": "attach",
      "name": "Wait for Minecraft Debug Connections",
      "mode": "listen",
      "localRoot": "${workspaceFolder}/",
      "port": 19144
    }
  ]
}
```

![launchjson.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/launchjson.png)

#### Шаг 5. Запустите ваш пакет параметров Minecraft

Теперь, когда вы подготовили Visual Studio Code и подготовили ваш Behavior Pack, вы готовы начать отладку!

Сначала нажмите **Start Debugging** внутри Visual Studio Code. Это переведет Visual Studio Code в режим *прослушать
подключение для отладки*.

Запустите Minecraft и загрузитесь в мир с вашим скриптовым пакетом параметров. Возможно, вы захотите установить точку
останова внутри вашей функции GameTest. Для этого щелкните слева от определенных строк кода, где вы хотите установить
точку останова.

Метки остановки, установленные в Visual Studio Code

![listenandbreakpoints.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/listenandbreakpoints.png)

Используйте эту команду с косой чертой для подключения к Visual Studio Code через порт.

`/script debugger connect localhost 19144`.

Вы должны увидеть ответ об успешном подключении от команды slash.

Теперь запустите код (вероятно, выполнив тест, например, `/gametest run (имя моего теста)`).

Вы должны увидеть, что ваши точки останова сработали. Вы также можете просматривать локальные переменные и добавлять
наблюдения по мере необходимости.

![breakpointhit.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/breakpointhit.png)

### Отладка на выделенном сервере Bedrock для Minecraft

Процедура отладки на Bedrock Dedicated Server немного отличается. При отладке с Bedrock Dedicated Server, Bedrock
Dedicated Server будет прослушивать отладочные соединения, инициированные из Visual Studio Code. Для начала вам нужно
установить отладчик Minecraft Bedrock Edition Debugger for Visual Studio Code, как описано выше.

#### Настройте свой выделенный сервер Bedrock.

По умолчанию выделенные серверы Bedrock не настроены на разрешение отладочных соединений. Чтобы включить отладку, вам
нужно изменить некоторые настройки в файле `server.properties` вашего Bedrock Dedicated Server.

Эти параметры настраивают отладку на Bedrock Dedicated Server:

1. `allow-outbound-script-debugging` (true/false) - включает команду подключения /script debugger. По умолчанию
   установлено значение false.
2. `allow-inbound-script-debugging` (true false) - включает команду /script debugger listen (и открытие портов на
   сервере). По умолчанию имеет значение false.
3. `force-inbound-debug-port` (число) - фиксирует порт входящей отладки на определенном порту. Это установит порт
   отладки сценария по умолчанию и не позволит пользователю команды /script debugger listen указать альтернативный порт.

Для данного проекта мы можем просто установить allow-inbound-script-debugging в true.

![serverproperties.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/serverproperties.png)

#### Подготовьте проект Behavior Pack.

Ваш экземпляр Visual Studio Code должен указывать на корень вашего пакета параметров в папке development_behavior_packs
экземпляра Minecraft (таким образом, вы должны открыть Visual Studio code по
адресу `(моя установка Bedrock Dedicated Server)\development_behavior_packs\(behaviorpackname)`).

В корне пакета параметров, который вы хотите отлаживать, добавьте подпапку .vscode. Добавьте следующий файл launch.json
в папку .vscode: (ПРИМЕЧАНИЕ: вам не нужно редактировать никакие строки этого файла).

``` json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "minecraft-js",
      "request": "attach",
      "name": "Attach to Minecraft Bedrock Dedicated Server",
      "localRoot": "${workspaceFolder}/",
      "port": 19144
    }
  ]
}
```

#### Запустите свой набор параметров Minecraft

Теперь, когда вы подготовили Visual Studio Code и подготовили свой пакет параметров, вы готовы начать отладку!

Запустите Minecraft и загрузитесь в мир с вашим скриптовым пакетом параметров.

В консоли Bedrock Dedicated Server используйте эту команду через слеш, чтобы начать прослушивание порта:

`script debugger listen 19144`.

Вы должны увидеть ответ "Debugger listening" от этой команды.

![serverdebuggerlistening.png](https://docs.microsoft.com/ru-ru/minecraft/creator/documents/media/scriptdevelopertools/serverdebuggerlistening.png)

Теперь нажмите кнопку "Start Debugging" внутри Visual Studio Code.

Вы можете запускать команды в Bedrock Dedicated Server для инициирования тестов,
например, `/gametest run (имя теста)`.

Вы можете установить точки остановки в коде, щелкнув в левой части редактора на определенных строках кода. По мере
выполнения тестов в пакете поведения ваши точки остановки должны сбиваться. Вы также можете просматривать локальные
переменные и добавлять наблюдения по мере необходимости.

Вот и все! Мы надеемся, что благодаря обновленным помощникам при добавлении строк JavaScript и новым возможностям
отладчика в Visual Studio Code вы сможете быстрее писать более объемные тесты и сценарии.
