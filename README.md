#include <stdio.h>
#define MAX_CONTESTANTS 8



// Function to cast a vote
void CastVote(int votes[], int contestantCount)
 {
    int choice;
    printf("Enter the contestant number you want to vote for: ");
    scanf("%d", &choice);

    // Validate the user's choice
    if (choice >= 1 && choice <= contestantCount) {
        votes[choice - 1]++;
        printf("Vote cast successfully!\n");
    } else {
        printf("Invalid choice. Please enter a valid contestant number.\n");
    }
}

// Function to show the total votes for each contestant
void ShowResults(int votes[], char contestants[][50], int contestantCount) {
    printf("Voting Results:\n");
    for (int i = 0; i < contestantCount; i++) {
        printf("%s: %d votes\n", contestants[i], votes[i]);
        
    }
}

// Function to show the contestants
void ShowContestants(char contestants[][50], int numContestants)
 {
    printf("Contestants:\n");
    for (int i = 0; i < numContestants; i++) {
        printf("%d. %s\n", i + 1, contestants[i]);
    }
}
int main() {
    char contestants[MAX_CONTESTANTS][50];
    int votes[MAX_CONTESTANTS] = {0};
    int numContestants;

    // Get the number of contestants
    printf("Enter the number of contestants (up to %d): ", MAX_CONTESTANTS);
    scanf("%d", &numContestants);

    // Validate the number of contestants
    if (numContestants < 1 || numContestants > MAX_CONTESTANTS) {
        printf("Invalid number of contestants. Exiting program.\n");
        return 1;  // Exit with an error code
    }

    // Get the names of the contestants
    for (int i = 0; i < numContestants; i++) {
        printf("Enter the name of contestant %d: ", i + 1);
        scanf("%s", contestants[i]);
    }

    int choice;
    do {
        // Show menu
        printf("\nMenu:\n");
        printf("1. Show Contestants\n");
        printf("2. Cast Vote\n");
        printf("3. Show Results\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                ShowContestants(contestants, numContestants);
                break;
            case 2:
                CastVote(votes, numContestants);
                break;
            case 3:
                ShowResults(votes, contestants, numContestants);
                break;
            case 4:
                printf("voting finished thanku \n");
                break;
            default:
                printf("Invalid choice. Please enter a valid option.\n");
        }
    } while (choice != 4);

    return 0;  
}
