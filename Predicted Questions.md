Questions from the WikiBooks page
## Question 1 - Symbol Case
Lower case symbols are not accepted as inputs. Fix this.
```cs
private string GetSymbolFromUser()
{
     string Symbol = "";
     while (!AllowedSymbols.Contains(Symbol))
     {
          Console.Write("Enter symbol: ");
          Symbol = Console.ReadLine().ToUpper();
      }
      return Symbol;
}

```
## Question 2 - Game file not existing
If a filename is entered that does not exist, the game is unplayable (infinite loop). Amend the program so that in this case the default game is played, with a suitable message to indicate this.

```cs
static void Main(string[] args)
        {
            string Again = "y";
            int Score;
            while (Again == "y")
            {
                Console.Write("Press Enter to start a standard puzzle or enter name of file to load: ");
                string Filename = Console.ReadLine();
                Puzzle MyPuzzle;
                if (Filename.Length > 0)
                {
                    try {
                        MyPuzzle = new Puzzle(Filename + ".txt");
                    }
                    catch {
                        Console.WriteLine("Invalid filename. Defaulting to standard puzzle");
                        MyPuzzle = new Puzzle(8, Convert.ToInt32(8*8*0.6));
                    }
                }
                else
                {
                    MyPuzzle = new Puzzle(8, Convert.ToInt32(8 * 8 * 0.6)); // 8*8 is the size of the grid, 0.6 is some kind of difficulty modifier, maybe?
                }
                //rest of main
            }
            Console.ReadLine();
        }
```
NB: The `try/catch` pair must be removed from the `LoadPuzzle()` subroutine in order for this method to work. Otherwise, the `LoadPuzzle()` pair will stop proper execution.
## Question 3 - Blow up a blocked cell
Have a 'bomb' that can remove or 'blow-up' a block in a 'blocked cell', but costs you some of your score (minus some points)
```cs

```
## Question 4 - Add additional symbols
Add additional letters/symbols e.g. L or O or U or V or C or H or I.
```cs

```
