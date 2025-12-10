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
    int len = strlen(text);
    char rail[key][len];

    // Fill with placeholder
    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';

    int dir_down = 0, row = 0;

    for (int col = 0; col < len; col++) {
        if (row == 0 || row == key - 1)
            dir_down = !dir_down;

        rail[row][col] = text[col];
        row += dir_down ? 1 : -1;
    }

    printf("\nCiphertext: ");
    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
}

int main() {
    char text[100];
    int key;

    printf("Enter the plaintext: ");
    fgets(text, sizeof(text), stdin);

    // Remove newline
    text[strcspn(text, "\n")] = '\0';

    printf("Enter number of rails: ");
    scanf("%d", &key);

    encryptRailFence(text, key);

    return 0;
}

```

# OUTPUT
<img width="462" height="253" alt="image" src="https://github.com/user-attachments/assets/0cda8107-54f4-496a-85f9-6390111008b2" />



# RESULT
Thus writing a C program to implement the rail fence transposition technique is Successfully done.

