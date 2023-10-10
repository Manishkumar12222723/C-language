# C-language
Creating tournament scheduler using C language




#include <stdio.h>
#include <string.h>

// Constants
#define MAX_TEAMS 20
#define MAX_TEAM_NAME_LENGTH 30
#define MAX_PLAYER_NAME_LENGTH 30
#define MAX_MATCHES_PER_DAY 2

// Global variables
char teamNames[MAX_TEAMS][MAX_TEAM_NAME_LENGTH];
char playerNames[MAX_TEAMS][MAX_PLAYER_NAME_LENGTH];
int numTeams = 0;
int numMatchesPerDay = 0;

// Function prototypes
void displayTeamsAndPlayers();
void addTeam();
void deleteAndUpdateTeam();
void generateSchedule();
void updateSchedule();

int main() {
    int choice;
    do {
        printf("\nIPL Cricket Tournament Scheduler\n");
        printf("1. Display the names of all the teams and their players\n");
        printf("2. Add a team to the tournament\n");
        printf("3. Delete and update team details\n");
        printf("4. Generate the schedule\n");
        printf("5. Update the schedule\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch(choice) {
            case 1:
                displayTeamsAndPlayers();
                break;
            case 2:
                addTeam();
                break;
            case 3:
                deleteAndUpdateTeam();
                break;
            case 4:
                generateSchedule();
                break;
            case 5:
                updateSchedule();
                break;
            case 6:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
                break;
        }
    } while (choice != 6);
    return 0;
}

void displayTeamsAndPlayers() {
    if (numTeams == 0) {
        printf("No teams added yet.\n");
    } else {
        printf("Teams and Players:\n");
        for (int i = 0; i < numTeams; i++) {
            printf("Team Name: %s\n", teamNames[i]);
            printf("Players: %s\n", playerNames[i]);
        }
    }
}

void addTeam() {
    if (numTeams == MAX_TEAMS) {
        printf("Maximum number of teams reached.\n");
        return;
    }

    printf("Enter team name: ");
    scanf(" %[^\n]s", teamNames[numTeams]);
    printf("Enter player names (separated by commas): ");
    scanf(" %[^\n]s", playerNames[numTeams]);
    numTeams++;
}

void deleteAndUpdateTeam() {
    if (numTeams == 0) {
        printf("No teams added yet.\n");
        return;
    }

    char teamName[MAX_TEAM_NAME_LENGTH];
    printf("Enter team name: ");
    scanf(" %[^\n]s", teamName);

    int teamIndex = -1;
    for (int i = 0; i < numTeams; i++) {
        if (strcmp(teamNames[i], teamName) == 0) {
            teamIndex = i;
            break;
        }
    }

    if (teamIndex == -1) {
        printf("Team not found.\n");
        return;
    }

    printf("1. Update team name\n");
    printf("2. Update player names\n");
    printf("Enter your choice: ");
    int choice;
    scanf("%d", &choice);

    switch(choice) {
        case 1:
            printf("Enter new team name: ");
            scanf(" %[^\n]s", teamNames[teamIndex]);
            break;
        case 2:
            printf("Enter new player names (separated)");
    }
}
