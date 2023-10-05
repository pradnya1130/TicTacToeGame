import tkinter as tk
from tkinter import messagebox

# Create the main window
window = tk.Tk()
window.title("Tic-Tac-Toe")

# Initialize variables
current_player = 'X'
board = [' ' for _ in range(9)]
scores = {'X': 0, 'O': 0, 'tie': 0}

# Define winning combinations
winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                        (0, 3, 6), (1, 4, 7), (2, 5, 8),
                        (0, 4, 8), (2, 4, 6)]

# Function to check for a winner
def check_winner(board):
    for combo in winning_combinations:
        if board[combo[0]] == board[combo[1]] == board[combo[2]] != ' ':
            return board[combo[0]]
    if ' ' not in board:
        return 'tie'
    return None

# Function to handle button click
def handle_click(index):
    global current_player

    if board[index] == ' ':
        board[index] = current_player
        buttons[index].config(text=current_player)
        winner = check_winner(board)
        if winner:
            if winner == 'tie':
                messagebox.showinfo("Game Over", "It's a tie!")
                scores['tie'] += 1
            else:
                messagebox.showinfo("Game Over", f"Player {winner} wins!")
                scores[winner] += 1
            reset_game()
            update_scores()
        else:
            current_player = 'O' if current_player == 'X' else 'X'

# Function to reset the game
def reset_game():
    global current_player, board
    current_player = 'X'
    board = [' ' for _ in range(9)]
    for button in buttons:
        button.config(text=' ', state=tk.NORMAL)

# Function to update the scores
def update_scores():
    score_label.config(text=f"Player X: {scores['X']}  Player O: {scores['O']}  Ties: {scores['tie']}")

# Create the buttons
buttons = []
for i in range(9):
    button = tk.Button(window, text=' ', width=10, height=5,
                      command=lambda i=i: handle_click(i))
    button.grid(row=i // 3, column=i % 3)
    buttons.append(button)

# Create the score label
score_label = tk.Label(window, text="Player X: 0  Player O: 0  Ties: 0")
score_label.grid(row=3, column=0, columnspan=3)

# Start the main loop
window.mainloop()
