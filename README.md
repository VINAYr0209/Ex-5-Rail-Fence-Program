# Ex-5-Rail-Fence-Program
IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

AIM:
To write a C program to implement the rail fence transposition technique.

DESCRIPTION:
In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

ALGORITHM:
STEP-1: Read the Plain text. 

STEP-2: Arrange the plain text in row columnar matrix format. STEP-3: Now read the keyword depending on the number of columns of the plain text. STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text. STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

PROGRAM

#include <stdio.h>
#include <string.h>
#define MAX 1000
#define RAILS 100
int main()
{
    char text[MAX];
    char matrix[RAILS][MAX] = {0};

    int key, row = 0;
    int direction = 1;
    int i, j, len;

    printf("Enter the Plain Text: ");
    fgets(text, MAX, stdin);

    text[strcspn(text, "\n")] = '\0';
    len = strlen(text);

    printf("Enter the Number of Rails: ");
    scanf("%d", &key);

    if (key < 1 || key > RAILS || key > len)
    {
        printf("Invalid number of rails!\n");
        return 1;
    }

    for (i = 0; i < len; i++)
    {
        matrix[row][i] = text[i];

        if (row == 0)
            direction = 1;
        else if (row == key - 1)
            direction = -1;

        row += direction;
    }

    printf("\nEncrypted Cipher Text: ");

    for (i = 0; i < key; i++)
    {
        for (j = 0; j < len; j++)
        {
            if (matrix[i][j] != '\0')
                printf("%c", matrix[i][j]);
        }
    }

    printf("\n");
    return 0;
}
OUTPUT
Enter the Plain Text: WEAREDISCOVEREDFLEEATONCE

Enter the Number of Rails: 3

Encrypted Cipher Text: WECRLTEERDSOEEFEAOCAIVDEN
RESULT
Thus, the C program to implement the Rail Fence Transposition Encryption Technique was successfully written, compiled and executed, and the plaintext was converted into ciphertext using the specified number of rails.
