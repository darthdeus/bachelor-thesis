# Using procedural content generation to balance encounters in RPG-like games

### Jakub Arnold


## Abstract:

Procedural content generation (PCG) is mostly examined in the context of map/environment creation, and not focusing on generating the actual game characters. The topic of this thesis is to explore PCG options for balancing encounters in turn-based RPG-like games. Part of the work is also designing a simple game with flexible enough mechanics so that different approaches to PCG can be tested easily. The game consists of a hex-based arena in which two teams fight, each consisting of a few charactes with unique abilities. We test the generated team setup using simulated AI vs AI combat, which shows that for most initial configurations there exists an equally strong, but different opponent.

## Introduction:

An increasing number of computer games is using procedural content generation (PCG) as one of their core mechanics. This can be in different contexts, most commonly for generating new levels (Diablo [Xcitace]). Occasionally games even generate player collectible items (Borderlands [Xcitace]), but there has not been much research on the use of procedural generation for balancing encounters in RPG games. By this we mean procedurally generating enemies that can be defeated by the player, but pose a challenge. A crucial criteria here is that the balance is not simply achieved by creating the enemy as an exact clone of the player, but rather explore the search-space to find an enemy that is not only balanced, but also different from the player.

One particular application for this kind of PCG is automatic difficulty adjustments based on the player's skill. Another possible use could be automatic generation of new and unique enemies based on given constraints, which is the approach we chose in this thesis.

We have created a custom game with mechanics that are simple enough to simulate quickly, yet flexible enough to represent a large search space. There are two teams that fight in a hexagonal arena, each consists of a small number of player controlled *characters* (*mages*), and each mage has a small number of *abilities*. In each turn the player has control over one of his characters, and both move around the map and cast spells, in any order he wishes. The only limit is the number of *action points* the character has available, which are consumed both by movement and ability usage. The side that first eliminates the opposing team wins.

All information is visible to all players, and all actions are completely deterministic. There is no time limit for the player action, which means the player could theoretically calculate a perfect move given enough time.

The goal of this thesis is to explore PCG options for balancing encounters in turn-based RPG-like games. We design a simple game with flexible mechanics, and build an AI that can be used to approximate the player. We then use genetic algorithms to evolve balanced opponents for the given player team, using AI vs AI combat as a fitness function.

## Structure:

In **chapter 2** we begin by defining the scope of the work, the used methods, and list related work. **Chapter 3** follows by exploring our game mechanics in detail and explaining the choices behind them. Next in **chapter 4** we will go over implementation details of the methodology, such as how the game simulator is implemented, the choice of technology, and algorithm choices in the experiments.

**Chapter 5** describes what experiments have been done with results discussed in **chapter 6**. Lastly, **chapter 7** serves as the user and developer documentation, describing implementation detail not relevant to the methodology mentioned in **chapter 4**.

**Chapter 8** closes with a conclusion and possibilities for future work.
