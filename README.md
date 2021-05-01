# Parse-Text-File-into-Summary-Statistics
Take text file and parse it into useful summary statistics and plots
## The Task
“Dominion” is a card game where players build decks of cards from a common pool/supply to score victory points.  The object of the game is to build a deck which will score the most points at the end of the game in the most efficient manner possible.  Many people who play Dominion use a website called “dominion.games” to compete with players all around the world.  During games, the website keeps track of each action taken by a player in a game log.  The game log presents itself similarly to a chat log where each line of the log is an action taken by a player.  Despite being a valuable tool to players, the game log provides no summary statistics or figures for a player to analyze (either during a game or after the game has concluded).  If a player wanted to make use of such statistics, they would have to go through the game log line by line to reconstruct and summarize the game that was played.  I automated this process.
## Libraries
`Numpy` and `matplotlib.pyplot` are used for this project
```
# Import numpy and matplotlib
import matplotlib.pyplot as plt
import numpy as np
```
## Parsing the Text File
