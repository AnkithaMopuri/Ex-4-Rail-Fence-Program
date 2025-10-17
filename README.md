# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

void encryptRailFence(char text[], int key) {
    char rail[key][strlen(text)];
    int i, j;

    // Fill the rail matrix with '\n' (placeholder)
    for (i = 0; i < key; i++)
        for (j = 0; j < strlen(text); j++)
            rail[i][j] = '\n';

    int dir_down = 0;
    i = 0; // current row

    for (j = 0; j < strlen(text); j++) {
        // Change direction at the top or bottom rail
        if (i == 0 || i == key - 1)
            dir_down = !dir_down;

        rail[i][j] = text[j];

        // Move diagonally
        i += dir_down ? 1 : -1;
    }

    // Construct ciphertext by reading row-wise
    printf("\nCiphertext: ");
    for (i = 0; i < key; i++)
        for (j = 0; j < strlen(text); j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
}

int main() {
    char text[100];
    int key;

    printf("Enter the plaintext: ");
    gets(text);

    printf("Enter number of rails: ");
    scanf("%d", &key);

    encryptRailFence(text, key);

    return 0;
}

```

# OUTPUT
<img width="805" height="520" alt="image" src="https://github.com/user-attachments/assets/8feeb160-3dde-403c-b104-124210160f8a" />


# RESULT
Thus writing a C program to implement the rail fence transposition technique is Successfully done.

