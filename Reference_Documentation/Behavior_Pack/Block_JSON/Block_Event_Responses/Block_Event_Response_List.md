# Документация блока - Ответы на события блока

Ниже приведен список всех доступных реакций на события блока в Minecraft:Bedrock Edition для использования
с [триггерами блока](../Block_Triggers/Block_Trigger_List.md).

## Список ответов на события блока

| Name                                        | Default Value | Type        | Description                                                                             |
|---------------------------------------------|---------------|-------------|-----------------------------------------------------------------------------------------|
| [add_mob_effect](add_mob_effect.md)         | not set       | JSON Object | Apply mob effect to a target.                                                           |
| [damage](damage.md)                         | not set       | JSON Object | Deals damage to the target.                                                             |
| [decrement_stack](decrement_stack.md)       | not set       | JSON Object | Decrement item stack.                                                                   |
| [die](die.md)                               | not set       | JSON Object | Kill target. If the target is self and this is run from a block then destroy the block. |
| [play_effect](play_effect.md)               | not set       | JSON Object | Spawns a particle effect relative to the target position.                               |
| [play_sound](play_sound.md)                 | not set       | JSON Object | Play a sound relative to the target position.                                           |
| [remove_mob_effect](remove_mob_effect.md)   | not set       | JSON Object | Removes mob effect from the target.                                                     |
| [run_command](run_command.md)               | not set       | JSON Object | Triggers a slash command or a list of slash commands.                                   |
| [set_block](set_block.md)                   | not set       | JSON Object | Sets this block to another block type.                                                  |
| [set_block_at_pos](set_block_at_pos.md)     | not set       | JSON Object | Sets a block relative to this block to another block type.                              |
| [set_block_property](set_block_property.md) | not set       | JSON Object | Sets a block property on this block.                                                    |
| [spawn_loot](spawn_loot.md)                 | not set       | JSON Object | Spawn loot from block.                                                                  |
| [swing](swing.md)                           | not set       | JSON Object | Event causes the actor to swing.                                                        |
| [teleport](teleport.md)                     | not set       | JSON Object | Teleport a target randomly around destination point.                                    |
| [transform_item](transform_item.md)         | not set       | JSON Object | Transforms item into another item.                                                      |
