# Parse-Text-File-into-Summary-Statistics
Take text file and parse it into useful summary statistics and plots
## The Task
“Dominion” is a card game where players build decks of cards from a common pool/supply to score victory points.  The object of the game is to build a deck which will score the most points at the end of the game in the most efficient manner possible.  Many people who play Dominion use a website called “dominion.games” to compete with players all around the world.  During games, the website keeps track of each action taken by a player in a game log.  The game log presents itself similarly to a chat log where each line of the log is an action taken by a player.  Despite being a valuable tool to players, the game log provides no summary statistics or figures for a player to analyze (either during a game or after the game has concluded).  If a player wanted to make use of such statistics, they would have to go through the game log line by line to reconstruct and summarize the game that was played.  I automated this process.

My goal was to make Python code which would take the game log and turn it into a variety of useful summary statistics and plots. In Dominion, “treasure” cards are used to buy other cards and victory points.  Naturally, knowing the total treasure in your deck at any given time is useful information to ascertain your deck’s “buying power”.  Knowledge of the total cards in a deck is also a useful metric for players to estimate probability of drawing a specific card or set of cards.  My first two sub-goals were to make a Python code which, when given the game log as an input, would produce a plot of total cards and treasure as a function of turn number for any given player.

## Libraries
`Numpy` and `matplotlib.pyplot` are used for this project.  They are imported and aliased as `np` and `plt`

```
# Import numpy and matplotlib
import matplotlib.pyplot as plt
import numpy as np
```
## Parsing the Text File
Game logs were downloaded as .txt files.  My first goal is to make a function which takes these files and parses them into a format that is easier to manipulate in Python, namely a `numpy` array:

```
# Function to parse each line in txt file into numpy array.  Input is a file path to the txt file
def text_gen(file):
    # Open and separate txt into array
    text = open(file)
    text_contents = text.read()
    sep_text = np.array(text_contents.splitlines())
    return np.array(sep_text)
```
The text file is selected and read using the `open()` and `.read()` commands.  `.splitlines()` takes the text and forms a list where each line is an element in the list.  The list is stored in a numpy array `np.array()`.  I refer to this as the **"Text Array"**, which will later be indexed and searched to produce the desired summary statistics.

## Index and Turn Number Arrays
Now that the Text Array is created, I want to be able to search it in a way that is useful.  The game log and therefore the Text Array provides information on the actions taken by **all** players in the game.  Since single player statistics are more useful to the individual player, I need to find a way to determine which elements of the Text Array correspond to a single player of interest.
