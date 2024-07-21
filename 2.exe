#include <stdio.h>
#include <stdlib.h>
 
// Define a structure for polynomial terms
typedef struct PolynomialTerm {
    int coefficient;
    int exponent;
    struct PolynomialTerm* next;
} PolynomialTerm;
 
// Define a structure for the polynomial linked list
typedef struct Polynomial {
    PolynomialTerm* head;
} Polynomial;
 
// Function prototypes
void insertTerm(Polynomial* poly, int coefficient, int exponent);
void displayPolynomial(Polynomial* poly);
Polynomial addPolynomials(Polynomial* poly1, Polynomial* poly2);
void insertTerm(Polynomial* poly, int coefficient, int exponent) {
    PolynomialTerm* newTerm = (PolynomialTerm*)malloc(sizeof(PolynomialTerm));
    newTerm->coefficient = coefficient;
    newTerm->exponent = exponent;
    newTerm->next = NULL;
 
    if (poly->head == NULL || poly->head->exponent < exponent) {
        newTerm->next = poly->head;
        poly->head = newTerm;
    } else {
        PolynomialTerm* current = poly->head;
        while (current->next != NULL && current->next->exponent > exponent) {
            current = current->next;
        }
        newTerm->next = current->next;
        current->next = newTerm;
    }
}
Polynomial addPolynomials(Polynomial* poly1, Polynomial* poly2) {
    Polynomial result;
    result.head = NULL;
    PolynomialTerm* term1 = poly1->head;
    PolynomialTerm* term2 = poly2->head;
 
    while (term1 != NULL && term2 != NULL) {
        if (term1->exponent == term2->exponent) {
            int sumCoeff = term1->coefficient + term2->coefficient;
            if (sumCoeff != 0) {
                insertTerm(&result, sumCoeff, term1->exponent);
            }
            term1 = term1->next;
            term2 = term2->next;
        } else if (term1->exponent > term2->exponent) {
            insertTerm(&result, term1->coefficient, term1->exponent);
            term1 = term1->next;
        } else {
            insertTerm(&result, term2->coefficient, term2->exponent);
            term2 = term2->next;
        }
    }
 
    while (term1 != NULL) {
        insertTerm(&result, term1->coefficient, term1->exponent);
        term1 = term1->next;
    }
 
    while (term2 != NULL) {
        insertTerm(&result, term2->coefficient, term2->exponent);
        term2 = term2->next;
    }
 
    return result;
}
void displayPolynomial(Polynomial* poly) {
    PolynomialTerm* current = poly->head;
    while (current != NULL) {
        if (current->coefficient > 0 && current != poly->head) {
            printf("+");
        }
        printf("%dx^%d ", current->coefficient, current->exponent);
        current = current->next;
    }
    printf("\n");
}
int main() {
    Polynomial poly1, poly2, result;
    poly1.head = NULL;
    poly2.head = NULL;
 
    int n, coefficient, exponent;
 
    printf("Enter the number of terms for the first polynomial: ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        printf("Enter coefficient and exponent: ");
        scanf("%d %d", &coefficient, &exponent);
        insertTerm(&poly1, coefficient, exponent);
    }
 
    printf("Enter the number of terms for the second polynomial: ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        printf("Enter coefficient and exponent: ");
        scanf("%d %d", &coefficient, &exponent);
        insertTerm(&poly2, coefficient, exponent);
    }
 
    result = addPolynomials(&poly1, &poly2);
 
    printf("First Polynomial: ");
    displayPolynomial(&poly1);
 
    printf("Second Polynomial: ");
    displayPolynomial(&poly2);
 
    printf("Resultant Polynomial: ");
    displayPolynomial(&result);
 
    return 0;
}