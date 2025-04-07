# Ex--5-Rail-Fence-Program

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

int main() {
    int i, j, k, l;
    char a[100], c[100], d[100];

    printf("\n\t\tRAIL FENCE TECHNIQUE (2 Rails)\n");
    printf("\nEnter the input string: ");
    fgets(a, sizeof(a), stdin); // Read input string including spaces
    a[strcspn(a, "\n")] = '\0'; // Remove newline character if present

    l = strlen(a); // Get length of input

    // ---------- Encryption ----------
    for (i = 0, j = 0; i < l; i++) {
        if (i % 2 == 0) {
            c[j++] = a[i]; // Characters at even indices
        }
    }
    for (i = 0; i < l; i++) {
        if (i % 2 == 1) {
            c[j++] = a[i]; // Characters at odd indices
        }
    }
    c[j] = '\0'; // Null-terminate the encrypted string

    printf("\nEncrypted text (Cipher text): %s\n", c);

    // ---------- Decryption ----------
    if (l % 2 == 0) {
        k = l / 2; // If even length
    } else {
        k = (l / 2) + 1; // If odd length
    }

    for (i = 0, j = 0; i < k; i++) {
        d[j] = c[i];
        j += 2; // Fill even positions
    }
    for (i = k, j = 1; i < l; i++) {
        d[j] = c[i];
        j += 2; // Fill odd positions
    }
    d[l] = '\0'; // Null-terminate the decrypted string

    printf("\nDecrypted text (Original): %s\n", d);

    return 0;
}

```

# OUTPUT
![image](https://github.com/user-attachments/assets/6e2abb3d-e99b-4bd0-8627-51922dfdf614)



# RESULT
The Program is executed successfully
