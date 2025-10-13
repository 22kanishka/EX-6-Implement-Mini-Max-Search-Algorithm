<h1>ExpNo 6 : Implement Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: KANISHKA P     </h3>
<h3>Register Number:2305001011       </h3>
<H3>Aim:</H3>
<p>
    Implement Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>

<H3>Theory and Procedure:</H3>

The Minimax Algorithm is a decision-making algorithm used in two-player games like Tic-Tac-Toe, Chess, and Checkers.
It helps the computer choose the best possible move by minimizing the opponent’s chance of winning while maximizing its own chance.

In Tic-Tac-Toe:

The human player is X (Minimizer).

The computer is O (Maximizer).

The algorithm explores all possible moves, checks who wins in each case, and backtracks to choose the optimal move.

<H3> Procedure: </H3>

Start the Game
Create a 3×3 Tic-Tac-Toe board and display it.

Player’s Move
The player enters their move (position 0–8).

Check for Win or Draw
After every move, check if either player has won or if the board is full.

Apply Minimax Algorithm

The computer simulates all possible moves.

For each move:

Temporarily play the move.

Recursively call Minimax to evaluate the outcome.

Undo the move and record the score.

Choose the move with the highest score (best for computer).

Computer’s Move
The best move chosen by Minimax is played by the computer.

Repeat
Alternate turns between player and computer until someone wins or the game ends in a draw.

Display Result
Print the final board and declare “X wins”, “O wins”, or “Draw”.

## program
```python
import math

b = [' ']*9

def show(): 
    for i in range(0,9,3): print(b[i], '|', b[i+1], '|', b[i+2])

def win(p):
    w = [(0,1,2),(3,4,5),(6,7,8),(0,3,6),(1,4,7),(2,5,8),(0,4,8),(2,4,6)]
    return any(b[x]==b[y]==b[z]==p for x,y,z in w)

def minimax(isMax):
    if win('O'): return 1
    if win('X'): return -1
    if ' ' not in b: return 0
    best = -math.inf if isMax else math.inf
    for i in range(9):
        if b[i]==' ':
            b[i]='O' if isMax else 'X'
            val=minimax(not isMax)
            b[i]=' '
            best = max(best,val) if isMax else min(best,val)
    return best

def best_move():
    best=-math.inf; move=-1
    for i in range(9):
        if b[i]==' ':
            b[i]='O'
            val=minimax(False)
            b[i]=' '
            if val>best: best,move=val,i
    return move

while True:
    show()
    if win('X') or win('O') or ' ' not in b: break
    p=int(input("Enter 0-8: "))
    if b[p]==' ': 
        b[p]='X'
        if not win('X') and ' ' in b: b[best_move()]='O'

show()
print("Winner:", "O" if win('O') else "X" if win('X') else "Draw")

```

<hr>
<h2>Sample Input and Output</h2>

<img width="287" height="503" alt="image" src="https://github.com/user-attachments/assets/52735d97-2312-4881-a036-bfe254484195" />


<hr>
<h2>Result:</h2>
<p>Thus,Implementation of  Minimax Search Algorithm for a Simple TIC-TAC-TOE game wasa done successfully.</p>
