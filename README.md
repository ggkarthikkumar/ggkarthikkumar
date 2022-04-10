#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{

    char str[64];
    char word[6][16];

    int i = 0;
    int j = 0;
    int k = 0;
    int l = 0;

    printf("Enter string: ");
    scanf("%[^\n]s", str);

    while (str[i] != 0) {
        if (str[i] == ' ') {
            word[k][j] = '\0';
            k++;
            j = 0;
        }
        else {
            word[k][j] = str[i];
            j++;
        }
        i++;
    }
    word[k][j] = '\0';

    j = 0;
    for (i = 0; i < k; i++) {
        int present = 0;
        for (l = 1; l < k + 1; l++) {
            if (word[l][j] == '\0' || l == i)
                continue;

            if (strcmp(word[i], word[l]) == 0) {
                word[l][j] = '\0';
                present = present + 1;
            }
        }
    }

    j = 0;
    printf("Result is:\n");
    for (i = 0; i < k + 1; i++) {
        if (word[i][j] == 0)
            continue;
        else
            printf("%s ", word[i]);
    }
    printf("\n");

    return 0;
}
