# 2024Prerelease
here we go 
## Puzzle Class
### Fields
#### Score
Integer that represents the current score of the puzzle being completed.
#### SymbolsLeft
Integer that represents the number of "moves" the player has left/the number of symbols the player can place.
#### GridSize
Integer that represents the size of the grid that is being played on.
#### Grid
List of Cell objects that represents the grid
#### AllowedPatterns
List of Pattern objects that define the allowed patterns in the grid
#### AllowedSymbols
List of strings that defines the allowed symbols 
### Methods
#### Constructor(s)
Filename constructor is used if a puzzle is created from a pre-existing file, otherwise the second constructor with the two integers is used. The filename constructor uses the LoadPuzzle() method, which will be elaborated on later. The second constructor, which is called to create a randomised, standard puzzle with 64 squares and 38 symbol moves. This constructor is only called in one place, so the Size parameter is always 8, and the StartSymbols parameter is always 38. I'm not entirely sure why they passed it through as ```Convert.ToInt32(8 * 8 * 0.6)```, but I guess we have to deal with it (TODO: Replace with 38 and see if anything changes)