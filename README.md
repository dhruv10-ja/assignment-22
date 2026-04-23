#include <stdio.h>
#include <string.h>

void menu();

int main() {
    char str1[100], str2[100], temp[100];
    int choice;

    while (1) {
        menu();
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar(); // Consumes the newline character left by scanf

        switch (choice) {
            case 1:
                printf("Enter string: ");
                fgets(str1, sizeof(str1), stdin);
                str1[strcspn(str1, "\n")] = 0; // Remove newline
                printf("Length of string: %zu\n", strlen(str1));
                break;

            case 2:
                printf("Enter source string: ");
                fgets(str1, sizeof(str1), stdin);
                str1[strcspn(str1, "\n")] = 0;
                strcpy(str2, str1);
                printf("String copied! Original: %s | Copied: %s\n", str1, str2);
                break;

            case 3:
                printf("Enter first string: ");
                fgets(str1, sizeof(str1), stdin);
                str1[strcspn(str1, "\n")] = 0;
                printf("Enter string to append: ");
                fgets(str2, sizeof(str2), stdin);
                str2[strcspn(str1, "\n")] = 0;
                strcat(str1, str2);
                printf("Concatenated string: %s\n", str1);
                break;

            case 4:
                printf("Enter first string: ");
                fgets(str1, sizeof(str1), stdin);
                str1[strcspn(str1, "\n")] = 0;
                printf("Enter second string: ");
                fgets(str2, sizeof(str2), stdin);
                str2[strcspn(str2, "\n")] = 0;
                if (strcmp(str1, str2) == 0)
                    printf("Strings are equal.\n");
                else
                    printf("Strings are not equal.\n");
                break;

            case 5:
                printf("Enter string to reverse: ");
                fgets(str1, sizeof(str1), stdin);
                str1[strcspn(str1, "\n")] = 0;
                // strrev is not standard C (ANSI), so we use a quick swap loop
                int len = strlen(str1);
                for(int i = 0; i < len/2; i++) {
                    char t = str1[i];
                    str1[i] = str1[len - 1 - i];
                    str1[len - 1 - i] = t;
                }
                printf("Reversed string: %s\n", str1);
                break;

            case 6:
                printf("Exiting program. Happy coding!\n");
                return 0;

            default:
                printf("Invalid choice! Please try again.\n");
        }
        printf("\n------------------------------\n");
    }
    return 0;
}

void menu() {
    printf("\n--- String Operations Menu ---\n");
    printf("1. Length (strlen)\n");
    printf("2. Copy (strcpy)\n");
    printf("3. Concatenation (strcat)\n");
    printf("4. Comparison (strcmp)\n");
    printf("5. Reverse\n");
    printf("6. Exit\n");
}
