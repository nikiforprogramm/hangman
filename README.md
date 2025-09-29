# hangman
def hangman():
    word_list = ["яблоко","гранит","резьба","машина", "дом", "кот", "сок", "лук", "сад", "нос", "рот", "год", "день", "ночь","река", "море", "лес", "снег", "дождь", "ветер", "птица", "рыба", "собака", "кошка","стол", "стул", "дверь", "окно", "пол", "потолок", "лампа", "книга", "ручка", "тетрадь","груша", "вишня", "слива", "морковь", "луна", "солнце", "звезда", "небо", "земля""огонь", "вода", "воздух", "цвет", "лист", "трава", "цветок", "роза", "роза", "ромашка","брат", "сестра", "мама", "папа", "друг", "гость", "учитель", "врач", "повар", "писатель","нога", "рука", "голова", "спина", "живот", "сердце", "глаз", "ухо", "нос", "рот", "утро", "вечер", "зима", "весна", "лето", "осень", "понедельник", "вторник", "среда", "четверг""пятница", "суббота", "воскресенье", "час", "минута, неделя, месяц,", "секунда", "радость", "смех", "песня", "танец"
,]
    random_number = random.randint(0, 101)
    word = word_list[random_number]
    wrong_guesses = 0
    stages = ["", "________      ", "|      |      ", "|      |      ", "|      |      ", "|      0      ", "|     /|\     ", "|     / \     ", "|"]
    remaining_letters = list(word)
    letter_board = ["__"] * len(word)
    win = False
    print('Добро пожаловать на казнь!')
    while wrong_guesses < len(stages) - 1:
        print('\n')
        guess = input("Введите букву: ")
        if guess in remaining_letters:
            character_index = remaining_letters.index(guess)
            letter_board[character_index] = guess
            remaining_letters[character_index] = '$'
        else: 
            wrong_guesses += 1
        print((' '.join(letter_board)))
        print('\n'.join(stages[0: wrong_guesses + 1]))
        if '__' not in letter_board:
            print('Вы выйграли! Было загадоно слово: ')
            print(' '.join(letter_board))
            win = True
            break
    if not win:
        print('\n'.join(stages[0: wrong_guesses]))
        print('Вы проиграли! Было загаданно слово {}'.format(word))
    restart = input("\nСыграем еще раз? (да/нет): ").lower()
    if restart == 'да':
        hangman()
    else:
        print("\nСпасибо за игру!")


hangman()


