AI Puzzle Solvers

Project Overview

This project, developed by Enugula Venu (ID: B211076, Class: E3 CSE C2), implements solutions to two classic AI search problems: the Bridge-Crossing Puzzle and the Rabbit Puzzle. Both puzzles are solved using the Breadth-First Search (BFS) algorithm  and DFS(Depth First Search) to find the  path to the goal state. The implementation is provided in a Jupyter notebook (ai.ipynb) using Python.

Bridge-Crossing Puzzle

Problem Description

The bridge-crossing puzzle involves four people (Amogh, Ameya, Grandmother, Grandfather) who must cross a bridge from the left side to the right side within 60 minutes. The bridge can only be crossed with an umbrella (e.g., a flashlight), and at most two people can cross at a time. Each person has a specific crossing time:

Amogh: 5 minutes
Ameya: 10 minutes
Grandmother: 20 minutes
Grandfather: 25 minutes

When two people cross together, the crossing time is the maximum of their individual times. After crossing to the right, one person must return to the left with the umbrella to allow further crossings. The goal is to have all four people on the right side within 60 minutes.

Approach

State Representation: Each state is represented by a BridgeState class, which tracks:

The position of each person ("left" or "right") in a dictionary.
The total time elapsed.
The umbrella’s side ("left" or "right").

Move Generation: The moveGen method generates valid next states:

From the left side, two distinct people cross to the right with the umbrella, taking the maximum of their crossing times.

From the right side, one person returns to the left with the umbrella, taking their individual crossing time.
States exceeding 60 minutes are pruned.


State Comparison: States are compared using __eq__ and __hash__ to avoid revisiting duplicates, considering positions, time, and umbrella side.


Path Reconstruction: The reconstructPath function traces back from the goal state to the initial state to display the solution path.


Rabbit Puzzle

Problem Description

The rabbit puzzle involves three rabbits on the left (L) and three rabbits on the right (R) on a 7-position linear board with one empty space (_). The initial state is RRR_LLL, and the goal is to reach LLL_RRR. Rabbits can move by:


Sliding into the adjacent empty space (move by 1 position).

Jumping over one rabbit to the empty space (move by 2 positions).

Approach

State Representation: Each state is represented by a RabbitState class, which stores the board as a 7-element list (e.g., ['R', 'R', 'R', '_', 'L', 'L', 'L']).

Move Generation: The moveGen method generates next states by:

Identifying the empty space’s index.

Allowing moves in four directions (-1, -2, +1, +2) if within bounds.

Permitting slides (move by 1) or jumps (move by 2 over a rabbit).

Swapping the empty space with the rabbit at the new position.

State Validation: The constructor ensures the state is valid (7 positions, 3 L, 3 R, 1 _).

State Comparison: States are compared using __eq__ and __hash__ based on the board configuration.

Path Reconstruction: The same reconstructPath function is used to display the solution path.

