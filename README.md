# tic-tac
board = [' ' for _ in range(9)]  # 3x3 board
player = 'X'

def print_board():
    for i in range(0, 9, 3):
        print(f"{board[i]} | {board[i+1]} | {board[i+2]}")
        if i < 6:
            print("---------")

def check_win():
    # Check rows, columns, and diagonals
    win_conditions = [(0, 1, 2), (3, 4, 5), (6, 7, 8),  # rows
                      (0, 3, 6), (1, 4, 7), (2, 5, 8),  # columns
                      (0, 4, 8), (2, 4, 6)]  # diagonals
    for a, b, c in win_conditions:
        if board[a] == board[b] == board[c] != ' ':
            return True
    return False

def is_board_full():
    return ' ' not in board

while True:
    print_board()
    move = int(input(f"Player {player}, choose a position (1-9): ")) - 1
    if board[move] != ' ':
        print("That spot is taken. Try again.")
        continue

    board[move] = player
    if check_win():
        print_board()
        print(f"Player {player} wins!")
        break
    if is_board_full():
        print_board()
        print("It's a draw!")
        break

    player = 'O' if player == 'X' else 'X'  # Switch players
