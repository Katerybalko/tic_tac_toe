# tic_tac_toe
game
bord_size = 3
bord = [1,2,3,4,5,6,7,8,9]

def draw_bord ():
    print ('_' * 4 * bord_size)
    for i in range(bord_size):
        print((' ' * 3 + '|')*3)
        print('', bord[i*3], '|', bord[1 + i*3], '|', bord[2 + i*3], '|')
        print(('_' * 3 + '|') * 3)
def game_step(index, char):
    if (index > 9 or index < 1 or bord[index-1] in ('x', 'o')):
        return False
    bord[index-1] = char
    return True
def check_win():
    win = False
    win_combination = (
        (0, 1, 2 ), (3, 4, 5), (6, 7, 8), (0, 3, 6), (1, 4, 7), (2, 5, 8),
        (0, 4, 8), (2,4,6)
    )
    for pos in win_combination:
        if (bord[pos[0]] ==  bord[pos[1]] and bord[pos[1]] ==  bord[pos[2]]):
            win = bord[pos[0]]
    return win
def start_game():
    current_player = 'x'
    step = 1
    draw_bord()
    while (step<10) and (check_win() == False):
        index = input('Ходит игрок ' + current_player + '. Введит номер поля (0 - это выход из игры, если ты устал :)):')
        if (index == '0'):
            break
        if (game_step(int(index), current_player)):
           print ('Удачный ход!')
           if (current_player == 'x'):
               current_player = 'o'
           else:
               current_player = 'x'
           draw_bord()
           step += 1
        else:
           print('Неверный номер! Повтори!')
    if (step == 10):
        print('Ничья! Игра окончена! Победила дружба!')
    else:
        print('Поздравляю! Выиграш за ' + check_win())
print ('Привет!')
print('Сейчас я расскажу тебе, как мы будем играть.')
print('Я буду просить тебя вводить номер поля, '
      'куда ты хочешь поставить свой символ.')
print ('Пиши номер поля, а я вместо тебя буду ставить символ.')
print ('Начинаем!')

start_game()

