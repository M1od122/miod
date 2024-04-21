# Игровое поле
board = [' ' for _ in range(9)]

# Отображение игрового поля
def display_board():
    for i in range(0, 9, 3):
        print(f"{board[i]} | {board[i+1]} | {board[i+2]}")
        if i < 6:
            print("---------")

# Проверки победителя
def check_winner(board, player):
    winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                            (0, 3, 6), (1, 4, 7), (2, 5, 8),
                            (0, 4, 8), (2, 4, 6)]
    for w in winning_combinations:
        if board[w[0]] == board[w[1]] == board[w[2]] == player:
            return True
    return False

# Функция для игры
def play_game():
    current_player = 'X'
    is_winning = False
    display_board()

    while ' ' in board and not is_winning:
        move = int(input(f"Игрок {current_player}, введите номер клетки для вашего хода (от 0 до 8): "))
        if board[move] == ' ':
            board[move] = current_player
            display_board()
            is_winning = check_winner(board, current_player)
            if current_player == 'X':
                current_player = 'O'
            else:
                current_player = 'X'
        else:
            print("Клетка уже занята, выберите другую.")

    if is_winning:
        print(f"Игрок {current_player} победил!")
    else:
        print("Ничья.")

# Запуск игры
play_game()
