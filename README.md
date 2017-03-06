# Tic-Tac-Toe-game
Udemy-Python_Bootcamp-Milestone Project 1


        from __future__ import print_function
        import os
        clear = lambda: os.system('cls')
        clear()

# Function to display the playing board

    def display_board(board):
        clear()

        print(' ' + str(board[0]) + ' | ' + str(board[1]) + ' | ' + str(board[2]))
        print(' ' + str(board[3]) + ' | ' + str(board[4]) + ' | ' + str(board[5]))
        print(' ' + str(board[6]) + ' | ' + str(board[7]) + ' | ' + str(board[8]))

    pass
    board = ['']*10

# Function to choose markers for the players

    def player_input():
        global marker
        marker = ' '
        while marker not in ('X', 'O'):
            marker = raw_input('Players choose your markers:').upper()
            if marker == 'X':
                return ('X', 'O')
            elif marker == 'O':
                return ('O', 'X')

# Function to choose which player starts the game
    import random
    def choose_first():
        global x
        x = random.randint(0, 1)
        if x == 0:
            return 0
        elif x == 1:
            return 1


    ##choose_first()


# Function to put the marker on the board as desired by the player

    def place_marker(board, marker, position):

       board[position] = marker


# Function to check if the player has won the game

    def win_check(board, marker):
        if (board[0] == board[1] == board[2] == marker) | (board[3] == board[4] == board[5] == marker) | (
                    board[6] == board[7] == board[8] == marker) | (board[0] == board[3] == board[6] == marker) | (
                    board[1] == board[4] == board[7] == marker) | (board[2] == board[5] == board[8] == marker) | (
                    board[0] == board[4] == board[8] == marker) | (board[2] == board[4] == board[6] == marker):
            return 1
            # print ('You won the game. Do you want to play again?')
        else:
            return 0
            # print ('Continue the game')
    pass

    ##win_check(board, marker)


# Function to check whether the player's selected position is available or not

    def space_check(board, position):
        if board[position] == '':
            return 1

    #   print( 'The position is available')
    # else:
    # print ('Choose an other position')
    #  avail=[i for i in range (0,9) if board[i]=='']



# Function to check if the board is completely filled

    def full_board_check(board):
        avail = [i for i in range(0, 9) if board[i] == '']
        if avail==[]:
            return 1


# Function to ask the player which position he wants to choose

    def player_choice(board):
        #print('The available positions are: ' + str(avail))
        return  int(raw_input(' Please enter the next position you wish:'))
        if space_check(board,position):
             print('position available')
        else:
            print('choose an other position')


    ##player_choice(board)


# Function to ask the players if they want to play again

    def replay():
        global rep
        rep= raw_input('Do you want to play again? y or n:')
        if rep.lower() == 'y':
            return 1
        elif rep.lower() == 'n':
            return 0


# overall code to call the functions in order to have  sequential steps in the game

    clear()
    print('Welcome to Tic Tac Toe!')

    while True:
        board = ['']*10
        player = player_input()
        print('player 1 marker =' + str(player[0]) + ', player_2 marker = ' + str(player[1]))
        turn = choose_first()
        if turn==0:
            print('player 1 make a move')
        else:
            print('player 2 make a move')
        game_on = True
        while game_on:

        if turn ==0:
            position= player_choice(board)
            if space_check(board, position) and position>0 and position < 9:
                print('position available')
            else:
                print('choose an other position between 0 and 9')

            place_marker(board, player[0], position)
            display_board(board)
            y = win_check(board, player[0])
            if y==1:
                    print('You won the game.')
                    game_on= False
                    break;
            else:
                if full_board_check(board):
                    print ('the game is a draw')
                    break;

                else:
                    turn = 1
                    print ('It is your opponents turn')


            global avail
            avail = [i for i in range(0, 9) if board[i] == '']
            print('The available positions are: ' + str(avail))



        elif turn == 1:
            position=player_choice(board)
            if space_check(board, position) and position>0 and position < 9:
                print('position available')
            else:
                 print('choose an other position between 0 and 9')

            place_marker(board, player[1], position)
            display_board(board)
            y = win_check(board, player[1])
            if y==1:
                print('You won the game.')
                game_on= False
                break;
            else:
                    if full_board_check(board):
                        print ('the game is a draw')
                        break;


                    else:
                        turn =0
                        print('It is your opponents turn')



            avail = [i for i in range(0, 9) if board[i] == '']
            print('The available positions are: ' + str(avail))

    if not replay():
         break






















