<h1>ExpNo 6 : Implement Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: KANISHKA P     </h3>
<h3>Register Number: 2305001011      </h3>
<H3>Aim:</H3>
<p>
    Implement Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>

<H3>Theory </H3>

The Minimax Algorithm is a decision-making algorithm used in two-player games like Tic-Tac-Toe, Chess, and Checkers.
It helps the computer choose the best possible move by minimizing the opponent’s chance of winning while maximizing its own chance.

In Tic-Tac-Toe:

The human player is X (Minimizer).

The computer is O (Maximizer).

The algorithm explores all possible moves, checks who wins in each case, and backtracks to choose the optimal move.

<H3> Procedure: </H3>

1.Initialize the Game Board
Create a 3×3 board and display it with empty positions for the player and computer.

2.Input Player Move
Take the player’s move as input and mark it on the board.

3.Apply Minimax Algorithm
The computer simulates all possible moves, evaluates each outcome using the Minimax function, and selects the move with the best score.

4.Check Game Status
After every move, check if there is a winner or if the game is a draw.

5.Display Result
Continue alternating turns until the game ends, then display the final board and announce the result (Win, Lose, or Draw).

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
<h2> Output</h2>

<img width="229" height="415" alt="image" src="https://github.com/user-attachments/assets/e45a29fb-17fb-4130-b6a3-9b1fa4cda007" />

<hr>
<h2>Result:</h2>
<p>Thus,Implementation of  Minimax Search Algorithm for a Simple TIC-TAC-TOE game wasa done successfully.</p>
