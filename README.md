# Krest
Кре́стики-но́лики — логическая игра между двумя противниками на квадратном поле 3 на 3 клетки или бо́льшего размера (вплоть до «бесконечного поля»). 
Один из игроков играет «крестиками», второй — «ноликами». В традиционной китайской игре (Гомоку) используются чёрные и белые камни.

Правила игры:

Выигранная партия в крестики-нолики
Игроки по очереди ставят на свободные клетки поля 3×3 знаки (один всегда крестики, другой всегда нолики). 
Первый, выстроивший в ряд 3 своих фигуры по вертикали, горизонтали или диагонали, выигрывает. 
ервый ход делает игрок, ставящий крестики.



#Cоздаем переменную board
board = list(range(1, 10))

#Прописываем наше игровое поле 3х3
def draw_board(board):
    for i in range(3):
        print("|", board[0+i*3], "|", board[1+i*3], "|", board[2+i*3], "|")
        print("-------------")
        
        
#Зададим функцию хода 
def take_input(token):
    valid = False
    while not valid:
    
#Cоздадим переменную в численном типе ,куда мы хотим поставить X или 0
        player_answer = int(input(("Куда поставим" + token+"? ")))
        if player_answer >=1 and player_answer <=9:
            if str(board[player_answer-1]) not in "XO":
                board[player_answer - 1] = token
                valid = True
            else:
                print("Эта клетка уже занята")
        else:
            print("Некорректный ввод. Введите число от 1 до 9 для хода ")
            
#Функция на проверку выйгрыша 
def check_win(board):
    win_coord = ((0,1,2), (3,4,5), (6,7,8),(0,3,6),(1,4,7),(2,5,8),(0,4,8),(2,4,6))
    for each in win_coord:
        if board[each[0]] == board[each[1]] == board[each[2]]:
            return board[each[0]]
        return False
        
#Собирем все написанные функции
def main(board):
    win = False
    counter = 0
    while not win:
        draw_board(board)
        if counter % 2 == 0:
            take_input("X")
        else:
            take_input("O")
        counter += 1

        if counter > 4:
            tmp = check_win(board)
            if tmp:
                win = True
                print(tmp, "победа")
        if counter == 9:
            print("Ничья")
            
#Для вывода игрового поля 
    draw_board(board)

main(board)
