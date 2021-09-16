# Документация блока - Ответы на события блока

Ниже приведен список всех доступных реакций на события блока в Minecraft:Bedrock Edition для использования
с [триггерами блока](../Block_Triggers/Block_Trigger_List.md).

## Список ответов на события блока

| Имя                                         | Значение по умолчанию | Тип         | Описание                                                                    |
|---------------------------------------------|-----------------------|-------------|-----------------------------------------------------------------------------|
| [add_mob_effect](add_mob_effect.md)         | not set               | JSON Object | Наложить эффект моба на цель.                                               |
| [damage](damage.md)                         | not set               | JSON Object | Наносит урон цели.                                                          |
| [decrement_stack](decrement_stack.md)       | not set               | JSON Object | Уменьшает стек предметов.                                                   |
| [die](die.md)                               | not set               | JSON Object | Убить цель. Если цель - это я, и она запущена из блока, то уничтожить блок. |
| [play_effect](play_effect.md)               | not set               | JSON Object | Порождает эффект частиц относительно позиции цели.                          |
| [play_sound](play_sound.md)                 | not set               | JSON Object | Воспроизвести звук относительно позиции цели.                               |
| [remove_mob_effect](remove_mob_effect.md)   | not set               | JSON Object | Снимает эффект моба с цели.                                                 |
| [run_command](run_command.md)               | not set               | JSON Object | Запускает слэш-команду или список слэш-команд.                              |
| [set_block](set_block.md)                   | not set               | JSON Object | Устанавливает этот блок в другой тип блока.                                 |
| [set_block_at_pos](set_block_at_pos.md)     | not set               | JSON Object | Устанавливает блок относительно этого блока в другой тип блока.             |
| [set_block_property](set_block_property.md) | not set               | JSON Object | Устанавливает свойство блока для этого блока.                               |
| [spawn_loot](spawn_loot.md)                 | not set               | JSON Object | Порождает добычу из блока.                                                  |
| [swing](swing.md)                           | not set               | JSON Object | Событие вызывает раскачивание актера.                                       |
| [teleport](teleport.md)                     | not set               | JSON Object | Телепортирует цель случайным образом вокруг точки назначения.               |
| [transform_item](transform_item.md)         | not set               | JSON Object | Превращает предмет в другой предмет.                                        |
