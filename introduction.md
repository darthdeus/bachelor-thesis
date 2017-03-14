# Using procedural content generation to balance encounters in RPG-like games

Abstract:

Procedural content generation (PCG) is mostly examined in the context of map/environment creation, and not focusing on generating the actual game characters. The topic of this thesis is to explore PCG options for balancing encounters in turn-based RPG-like games. Part of the work is also designing a simple game with flexible enough mechanics so that different approaches to PCG can be tested easily. The game consists of a hex-based arena in which two teams fight, each consisting of a few charactes with unique abilities. We test the generated team setup using simulated AI vs AI combat, which shows that for most initial configurations there exists an equally strong, but different opponent.

Introduction:

An increasing number of computer games are using procedural content generation (PCG) as one of their core mechanics. This can be in different contexts, most commonly for generating new levels. Occasionally games even generate player collectible items, but there hasn't been much research on the use of procedural generation for balancing encounters in RPG games.

??? pozn.: proc se to nedela / neexistuje zadny paper na podobne tema? ???

One particular application for this kind of PCG is automatic difficulty adjustments based on player skill. Another possible use could be automatic generation of new and unique enemies based on given constraints, which is the approach we chose in this thesis.

??? pozn.: level designeri delaji vsechno rucne, PCG jim muze pomoct v toolech? ???

The goal of this thesis is to show how evolutionary algorithms together with Monte Carlo Tree Search (*MCTS*) can be used to create balanced encounters in turn-based RPG-like games. Another criteria is that each side of the encounter is different, and the balance is not achieved by simply mirroring the opponent.

We've created a custom game with mechanics that are simple enough to simulate quickly, yet flexible enough to represent a large search space.

There are two teams that fight in a hexagonal arena, each consists of a small number of player controlled characters (*mages*), and each mage has a small number of *abilities*. In each turn the player has control over one of his character, and both move around the map and cast spells, in any order he wishes. The only limit is the number of *action points* the character has available, which are consumed both by movement and ability usage. After the player finishes playing his *turn* (either because he has no more action points, or because he wishes to not do anything), the control goes to the next character, which is picked based on an initial order.

All information is visible to all players, and all actions are completely deterministic. There is no time limit for the player action, which means the player could theoretically calculate a perfect move given enough time. In practice there should be at last 5 possible actions in any given situation, and the player would generally perform at least 2-3 of those in his turn (move forward, use ability, move behind cover), having the game last for at least a few turns. This creates a large enough space to make complete search unfeasible in practice.

We've chosen to use MCTS to represent the artificial intelligence (*AI*) of a skilled player. We then compare it with rule based AIs to show that it performs well. *The experimentary results show that MCTS performs well enough to approximate the player.* (??? pozn: tohle jeste nemam ???)

The procedural generation is done using evolutionary algorithms, which begin by generating an initial randomized population. Each member of the population is characterized by his genes, which are altered throughout the evolution. During each step, the population is evaluated using a fitness function, which judges how well each member matches the criteria.

For our purposes, the fitness function describes how well balanced is the encounter, which is measured using MCTS and a handful of rule-based AIs. We also employ a few heuristics to make sure the encounters fulfill additional criteria, such as game length, etc.



---

~~The PCG algorithm takes one team as an input and generates a suitable opponent in a way that the resulting matchup is balanced, which is verified using AI vs AI gameplay.~~

- co je znamo
  - PCG se pouziva na mapy
  - PCG na postavy skoro nikdo nedela obecne, neumi se to?
  - PCG na cele hry se neumi

- cil prace
  - ukazat ze 1. a 2. plati? (viz dole)

- je to dulezite
  - siroke aplikace pro ruzne RPG hry
  - moznost pro prakticky neomezeny gameplay
  - hry ktere prizpusobuji obtiznost hraci podle toho, jak si hrac vybere

- volba metody
  - pouzivame MCTS pro simulaci hrace
  - pouzivame evoluci pro generovani balanced encounteru

  - 1. hypoteza: MCTS aproximuje hrace dostatecne dobre
    - jak to dokazu?
    - staci ukazat, ze MCTS porazi ruzne pravidlove AIcka? (potrebuju ruzne, nebo mi staci jedno?)

  - 2. hypoteza: vybrane herni mechaniky umoznuji aby dva velmi rozdilne tymy byly vyvazene
    - pokud MCTS funguje, tak staci pro statisticky vyznamny pocet dvojic ukazat, ze 2) plati?

  - 3. hypoteza: umim generovat dva ruzne tymy co maji ~50% winrate