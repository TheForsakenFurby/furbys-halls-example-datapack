# furbys-halls-example-datapack
**TL;DR: 1.21.5 datapack with a boring underground structure. Inteded for learning purposes.**

This datapack adds a simple, jigsaw-type underground structure to Minecraft worlds. It has two variants, both of which can appear in any biomes which have trial chambers. The structure is a sprawling system of plain, dark, hallways, with mob spawners and a loot room near the center. They come in default (regular hostile mob) and zombie-only versions. The loot is decent.

This datapack is published for learning purposes – i.e. those who download it are encouraged to delve into the datapack files to learn how they can add structures to their own datapacks. I can't really recommend actually playing with it, though I don't think it *detracts* from the vanilla experience at all.

If you have questions, feel free to message me on Discord. My account is `theforsakenfurby`

## Technical Clarifications
* Only guaranteed to work in Java Edition 1.21.5
* Unlikely to be updated
* This pack has two structure sets, with the same salt. It is generally NOT recommended to give structure sets the same salt, nor to reuse salts from vanilla. Salts are basically the "random seed" for the structure set, and giving two structure sets the same salt will cause the structures to appear in *the exact same spots*. I gave my structure sets the same salt because I *want* them to appear in the exact same spots, as one is a small surface feature, meant to signal that there's a halls structure underground.
* I personally create structures to be easily reconfigurable in JSON if I want to change something, rather than needing to resave the structure files. I do not know if this approach to structure creation is normal or advisable.
  * For example, my structure pieces contain marker entities, which I then have execute `/summon` commands via function – this way, if I want to change the entity, I can just change that command, rather than summon the new entity and resave the structure piece.
  * Similarly, my structure pieces have empty chests and mob spawners, which I append data to via processor list.
* The processor lists look daunting. This is because I go overkill with them. For example, there are 80 possible blockstate combinations for a stair block. Instead of going into my structure and checking which blockstates are actually in it, I have the processor list replace *each of the 80 possible combinations*. That way, I don't have to think about it if I tweak the structures or add new pieces with new blockstates.
  * I don't know if this is an advisable approach either. If you take this approach too, select-all, copy-paste, and find-all-replace are very useful time-savers.
  * Processor lists are lists of processors, and some of those processors can have many, many rules. To help with readability, I divide my processors by "function". For example, in my `default` processor list, one processor's job it to replace 37.5% of all stone brick type blocks (e.g. stairs, slabs, walls) with their mossy variants, and *nothing else*. Other processors in that list accomplish other functions.
