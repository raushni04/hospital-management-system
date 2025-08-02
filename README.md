# hospital-management-system
The Hospital Management System (HMS) is a C-based application designed to streamline hospital operations. It features patient registration, appointment scheduling, medical records management, and billing functionalities.
#include <stdio.h>
#include <string.h>

#define MAX_PATIENTS 100

typedef struct {
    int id;
    char name[50];
    int age;
    char gender[10];
    char medicalHistory[200];
} Patient;

Patient patients[MAX_PATIENTS];
int patientCount = 0;

void registerPatient() {
    if (patientCount < MAX_PATIENTS) {
        Patient newPatient;
        newPatient.id = patientCount + 1; // Simple ID assignment
        printf("Enter patient name: ");
        scanf("%s", newPatient.name);
        printf("Enter patient age: ");
        scanf("%d", &newPatient.age);
        printf("Enter patient gender: ");
        scanf("%s", newPatient.gender);
        printf("Enter medical history: ");
        scanf(" %[^\n]", newPatient.medicalHistory); // To read string with spaces

        patients[patientCount] = newPatient;
        patientCount++;
        printf("Patient registered successfully!\n");
    } else {
        printf("Patient limit reached!\n");
    }
}

int main() {
    int choice;
    do {
        printf("Hospital Management System\n");
        printf("1. Register Patient\n");
        printf("2. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                registerPatient();
                break;
            case 2:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 2);

    return 0;
}
