#include<stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
// Function to draw the Tic Tac Toe board
void drawBoard(char board[]) {


    printf("\n");
    for(int i=0;i<9;i++){
     if(board[i]=='X')
       printf("\033[38;5;13m");
     else if(board[i]>='1'&&board[i]<='9')
        printf("\033[38;5;4m");
      else
        printf("\033[38;5;160m");
     printf(" %c",board[i]);
     printf(" ");
     printf("\033[38;5;16m");
     if((i+1)%3!=0)
     printf("|");
     if((i+1)%3==0){
        printf("\n");
        printf("===|===|===\n");
        }
      printf("\033[38;5;16m");

    }



}

// Function to check if there's a winner
int checkWin(char board[], char mark) {
    if((board[0] == mark && board[1] == mark && board[2] == mark) ||  // top row
            (board[3] == mark && board[4] == mark && board[5] == mark) ||  // middle row
            (board[6] == mark && board[7] == mark && board[8] == mark) ||  // bottom row
            (board[0] == mark && board[3] == mark && board[6] == mark) ||  // left column
            (board[1] == mark && board[4] == mark && board[7] == mark) ||  // middle column
            (board[2] == mark && board[5] == mark && board[8] == mark) ||  // right column
            (board[0] == mark && board[4] == mark && board[8] == mark) ||  // diagonal
            (board[2] == mark && board[4] == mark && board[6] == mark))
            return 1;
      else if((board[0]!='1'&&board[1]!='2'&&board[2]!='3'&&board[3]!='4'&&
             board[4]!='5'&&board[5]!='6'&&board[6]!='7'&&board[7]!='8'&&
             board[8]!='9'))
             return 2;
      else
                return 0;
}

// Function to get a valid move from the user
int getUserMove(char board[]) {
    int choice;
    printf("Enter a number (1-9): ");
    scanf("%d", &choice);
    return choice;
}
// Function for the computer to make a move
int getComputerMove_easy(char board[]) {
    int move;
    do {
        move = rand() % 9;
    } while (board[move] != '1' + move);
    return move + 1;
}
int getComputerMove_medium(char board[]){
int move;
if(board[0]=='X'&&board[1]=='X'&&board[2]=='3')
    move=3;
else if(board[1]=='X'&&board[2]=='X'&&board[0]=='1')
    move=1;
else if(board[3]=='X'&&board[4]=='X'&&board[5]=='6')
    move=6;
else if(board[0]=='X'&&board[2]=='X'&&board[1]=='2')
    move=2;
else if(board[4]=='X'&&board[5]=='X'&&board[3]=='4')
    move=4;
else if(board[3]=='X'&&board[5]=='X'&&board[4]=='5')
    move=5;
else if(board[6]=='X'&&board[7]=='X'&&board[8]=='9')
    move=9;
else if(board[7]=='X'&&board[8]=='X'&&board[6]=='7')
    move=7;
else if(board[6]=='X'&&board[8]=='X'&&board[7]=='8')
    move=8;
else if(board[0]=='X'&&board[3]=='X'&&board[6]=='7')
    move=7;
else if(board[3]=='X'&&board[6]=='X'&&board[0]=='1')
    move=1;
else if(board[0]=='X'&&board[6]=='X'&&board[3]=='4')
    move=4;
else if(board[1]=='X'&&board[4]=='X'&&board[7]=='8')
    move=8;
else if(board[4]=='X'&&board[7]=='X'&&board[1]=='2')
    move=2;
else if(board[1]=='X'&&board[7]=='X'&&board[4]=='5')
    move=5;
else if(board[2]=='X'&&board[5]=='X'&&board[8]=='9')
    move=9;
else if(board[5]=='X'&&board[8]=='X'&&board[2]=='3')
    move=3;
else if(board[2]=='X'&&board[8]=='X'&&board[5]=='6')
    move=6;
else if(board[0]=='X'&&board[4]=='X'&&board[8]=='9')
    move=9;
else if(board[4]=='X'&&board[8]=='X'&&board[0]=='1')
    move=1;
else if(board[0]=='X'&&board[8]=='X'&&board[4]=='5')
    move=5;
else if(board[2]=='X'&&board[4]=='X'&&board[6]=='7')
    move=7;
else if(board[6]=='X'&&board[4]=='X'&&board[2]=='3')
    move=3;
else if(board[2]=='X'&&board[6]=='X'&&board[4]=='5')
    move=5;
else
    move=getComputerMove_easy(board);
return move;

}
int getComputerMove_hard(char board[]){
int move;
if(board[0]=='O'&&board[1]=='O'&&board[2]=='3')
    move=3;
else if(board[1]=='O'&&board[2]=='O'&&board[0]=='1')
    move=1;
else if(board[3]=='O'&&board[4]=='O'&&board[5]=='6')
    move=6;
else if(board[0]=='O'&&board[2]=='O'&&board[1]=='2')
    move=2;
else if(board[4]=='O'&&board[5]=='O'&&board[3]=='4')
    move=4;
else if(board[3]=='O'&&board[5]=='O'&&board[4]=='5')
    move=5;
else if(board[6]=='O'&&board[7]=='O'&&board[8]=='9')
    move=9;
else if(board[7]=='O'&&board[8]=='O'&&board[6]=='7')
    move=7;
else if(board[6]=='O'&&board[8]=='O'&&board[7]=='8')
    move=8;
else if(board[0]=='O'&&board[3]=='O'&&board[6]=='7')
    move=7;
else if(board[3]=='O'&&board[6]=='O'&&board[0]=='1')
    move=1;
else if(board[0]=='O'&&board[6]=='O'&&board[3]=='4')
    move=4;
else if(board[1]=='O'&&board[4]=='O'&&board[7]=='8')
    move=8;
else if(board[4]=='O'&&board[7]=='O'&&board[1]=='2')
    move=2;
else if(board[1]=='O'&&board[7]=='O'&&board[4]=='5')
    move=5;
else if(board[2]=='O'&&board[5]=='O'&&board[8]=='9')
    move=9;
else if(board[5]=='O'&&board[8]=='O'&&board[2]=='3')
    move=3;
else if(board[2]=='O'&&board[8]=='O'&&board[5]=='6')
    move=6;
else if(board[0]=='O'&&board[4]=='O'&&board[8]=='9')
    move=9;
else if(board[4]=='O'&&board[8]=='O'&&board[0]=='1')
    move=1;
else if(board[0]=='O'&&board[8]=='O'&&board[4]=='5')
    move=5;
else if(board[2]=='O'&&board[4]=='O'&&board[6]=='7')
    move=7;
else if(board[6]=='O'&&board[4]=='O'&&board[2]=='3')
    move=3;
else if(board[2]=='O'&&board[6]=='O'&&board[4]=='5')
    move=5;
else if(board[0]=='X'&&board[1]=='X'&&board[2]=='3')
    move=3;
else if(board[1]=='X'&&board[2]=='X'&&board[0]=='1')
    move=1;
else if(board[3]=='X'&&board[4]=='X'&&board[5]=='6')
    move=6;
else if(board[0]=='X'&&board[2]=='X'&&board[1]=='2')
    move=2;
else if(board[4]=='X'&&board[5]=='X'&&board[3]=='4')
    move=4;
else if(board[3]=='X'&&board[5]=='X'&&board[4]=='5')
    move=5;
else if(board[6]=='X'&&board[7]=='X'&&board[8]=='9')
    move=9;
else if(board[7]=='X'&&board[8]=='X'&&board[6]=='7')
    move=7;
else if(board[6]=='X'&&board[8]=='X'&&board[7]=='8')
    move=8;
else if(board[0]=='X'&&board[3]=='X'&&board[6]=='7')
    move=7;
else if(board[3]=='X'&&board[6]=='X'&&board[0]=='1')
    move=1;
else if(board[0]=='X'&&board[6]=='X'&&board[3]=='4')
    move=4;
else if(board[1]=='X'&&board[4]=='X'&&board[7]=='8')
    move=8;
else if(board[4]=='X'&&board[7]=='X'&&board[1]=='2')
    move=2;
else if(board[1]=='X'&&board[7]=='X'&&board[4]=='5')
    move=5;
else if(board[2]=='X'&&board[5]=='X'&&board[8]=='9')
    move=9;
else if(board[5]=='X'&&board[8]=='X'&&board[2]=='3')
    move=3;
else if(board[2]=='X'&&board[8]=='X'&&board[5]=='6')
    move=6;
else if(board[0]=='X'&&board[4]=='X'&&board[8]=='9')
    move=9;
else if(board[4]=='X'&&board[8]=='X'&&board[0]=='1')
    move=1;
else if(board[0]=='X'&&board[8]=='X'&&board[4]=='5')
    move=5;
else if(board[2]=='X'&&board[4]=='X'&&board[6]=='7')
    move=7;
else if(board[6]=='X'&&board[4]=='X'&&board[2]=='3')
    move=3;
else if(board[2]=='X'&&board[6]=='X'&&board[4]=='5')
    move=5;
else
    move=getComputerMove_easy(board);
return move;
}
int main() {
    system("cls");
    system("color 70");
    char board[9] = {'1', '2', '3', '4', '5', '6', '7', '8', '9'};
    int player = 1, choice, gameStatus = 0, opponentChoice;
    char mark,name_1[10],name_2[10];
    int level=0;
    srand(time(NULL)); // Seed for randomization
    printf("Choose opponent:\n");
    printf("1. Another player\n");
    printf("2. Play against the computer\n");
    scanf("%d", &opponentChoice);
    if(opponentChoice==1){
        printf("Enter player name -1:");
        scanf(" %[^\n]s",&name_1);
        printf("Enter player name -2:");
        scanf(" %[^\n]s",&name_2);
                }
    else{
        printf("Enter your name:");
        scanf(" %[^\n]s",name_1);
        printf("\nEnter your choice\n1.Easy\n2.Medium\n3.Hard\n");
        scanf("%d",&level);
        printf("\n\n");
    }
    do {
        drawBoard(board);
        player = (player % 2) ? 1 : 2;
        if(player!=1&&opponentChoice==1)
        {
            printf("%s's move\n",name_2);
        }
        if (opponentChoice == 1|| (opponentChoice == 2 && player == 1)) {
            if(player==1&&opponentChoice == 1||opponentChoice==2)
            {
            printf("%s's move\n",name_1);
            }
            choice = getUserMove(board);
          if (player==1)
            mark = 'X';
          else
             mark='O';
        }
        else if (level==1&&opponentChoice==2){
            choice = getComputerMove_easy(board);
            mark = 'O';
            printf("Computer chooses position %d\n", choice);
        }
        else if(level==2&&opponentChoice==2){
            choice=getComputerMove_medium(board);
            mark='O';
            printf("Computer chooses position %d\n", choice);
        }
        else if(level==3&&opponentChoice==2){
            choice=getComputerMove_hard(board);
            mark='O';
            printf("Computer chooses position %d\n",choice);
        }
        if (choice >= 1 && choice <= 9 && board[choice - 1] == '1' + choice - 1)
            board[choice - 1] = mark;
        else {
            printf("Invalid move! ");
            player--;
        }
        gameStatus = checkWin(board, mark);
        player++;
    } while (gameStatus == 0);
    drawBoard(board);

    if (gameStatus == 1&&opponentChoice==1){
        if(player-1==1)
            printf("%s Wins!\n",name_1);
        else
            printf("%s Wins!\n",name_2);
            }
   else if(gameStatus==1&&opponentChoice==2){
        if(player-1==1)
            printf("%s Wins!\n",name_1);
        else
            printf("Computer Wins!\n");

    }
    else if(gameStatus==2)
        printf("Game draw!\n");
    return 0;
}

