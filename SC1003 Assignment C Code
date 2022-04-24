  /*edit*/

/* Teo De Xuan Justin's code */
/* 20/10/2021 - Completed */
/* 20/10/2021 - Cleaned Somewhat */
/* 22/10/2021 - Rechecked for Case 10 (No Change) */

        /*end_edit*/
        /*edit*/
/*All Sample Test Cases Passed*/

#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdbool.h>

#define MAX 5
#define SENTINEL_INT 2147483647
/* NameCard structure (given) */
typedef struct
{
    int nameCardID;
    char personName[20];
    char companyName[20];
} NameCard;
NameCard stackOfCards[MAX];
 
/*Declare temp variables*/
int tempID = SENTINEL_INT; //sentinel value
char tempPersonName[20]="";
char tempCompanyName[20]="";

/* Function Prototypes */
void listNameCards();
void addNameCard();
void removeNameCard();
void getNameCard();
void sortNameCards();

int main()
{
    int response, i;
  
    /*Initialize NameCards to Empty*/
    for (i=0;i<MAX;i++) {
        stackOfCards[i].nameCardID = SENTINEL_INT;     // set to sentinel value
        strcpy(stackOfCards[i].personName,"");
        strcpy(stackOfCards[i].companyName,"");
    }
  
    /*Print Menu*/
    printf("NTU NAME CARD HOLDER MANAGEMENT PROGRAM: \n"
    "1: listNameCards()\n"
    "2: addNameCard()\n"
    "3: removeNameCard()\n"
    "4: getNameCard()\n"
    "5: quit\n");
  
    while ((response !=5)){
        sortNameCards();   // sorts NameCards before booting
        printf("Enter your choice: \n"); // only this line is displayed repeatedly
        scanf("%d", &response);
        if (response ==1){
            listNameCards();
        }
        else if (response ==2){
            addNameCard();
            sortNameCards();
        }
        else if (response ==3){
            removeNameCard();
            sortNameCards();
        }
        else if (response ==4){
            getNameCard();
        }
    }
    return 0;
}

void listNameCards(){
    printf("listNameCards():\n");
    int i;
    bool isEmpty = true;
    for (i=0;i<MAX;i++){
        if (stackOfCards[i].nameCardID != SENTINEL_INT){     //sentinel value
            isEmpty=false;
            break;
        }
        else
            continue;
    }
    //if empty, empty; if not empty, print list
    if (isEmpty) {
        printf("The name card holder is empty\n");
    }
    else
        for (i=0;i<MAX;i++){
            if (stackOfCards[i].nameCardID != SENTINEL_INT) {     //sentinel value
                printf("nameCardID: %d\npersonName: %s\ncompanyName: %s\n", stackOfCards[i].nameCardID,stackOfCards[i].personName,stackOfCards[i].companyName);
            }
            else{
                continue;
            }
        }
      
}

void addNameCard(){
    //modified to fulfil Test Case 5
    printf("addNameCard():\n");
    int i, j=0;
    bool isFull = true;
    bool isDuplicate = false;
  
    //check if full
    for (i=0;i<MAX;i++){
        if (stackOfCards[i].nameCardID == SENTINEL_INT){
            isFull=false;
            break;
        }
        else
            j++;        //counter for array index
            continue;
    }
  
    printf("Enter nameCardID: \n");
    scanf("%d", &stackOfCards[j].nameCardID);
  
    printf("Enter personName: \n");
    scanf("\n");                                                                         
    fgets(stackOfCards[j].personName,20,stdin);
    stackOfCards[j].personName[strcspn(stackOfCards[j].personName, "\n")] = 0;  // deletes the \n from stdin
  
    printf("Enter companyName: \n");         
    scanf("\n");
    fgets(stackOfCards[j].companyName,20,stdin);
    stackOfCards[j].companyName[strcspn(stackOfCards[j].companyName, "\n")] = 0; // deletes the \n from stdin  
  
    if (isFull) {
        printf("The name card holder is full\n");
        stackOfCards[j].nameCardID = SENTINEL_INT;     // set to sentinel value
        strcpy(stackOfCards[j].personName,"");
        strcpy(stackOfCards[j].companyName,"");
    }
    else {
        //check if same ID
        for (i=0;i<j;i++){           // j, not MAX!
            if (stackOfCards[j].nameCardID==stackOfCards[i].nameCardID){
                isDuplicate=true;
                stackOfCards[j].nameCardID=SENTINEL_INT; //undo the repetition
                break;
            }  else
                    continue;
        }
        if (isDuplicate){
            printf("The nameCardID has already existed\n");
        }   else {
                printf("The name card has been added successfully\n");
        }
      
    }
      
}

void removeNameCard(){
    int i=0;
    int j=0;
    char removeNameCardPersonName[20]="";
    char comparePersonName[20]="";
    bool gotRemove = false;                        
    bool isEmpty = true;
  
    printf("removeNameCard():\n");
    printf("Enter personName: \n");
    scanf("\n");                                                                      
    fgets(removeNameCardPersonName,20,stdin);
    removeNameCardPersonName[strcspn(removeNameCardPersonName, "\n")] = 0;  // deletes the \n from stdin
  
  
    while(removeNameCardPersonName[i]) {
    removeNameCardPersonName[i]=tolower(removeNameCardPersonName[i]);
    i++;
    }
  
    for(i=0;i<MAX;i++){
        strcpy(comparePersonName,stackOfCards[i].personName);
        j=0;
        while(comparePersonName[j]) {
        comparePersonName[j]=tolower(comparePersonName[j]);
        j++;
        }
      
        //!strcmp(comparePersonName,removeNameCardPersonName) returns 1 if strings match
        if( !strcmp(comparePersonName,removeNameCardPersonName) && (removeNameCardPersonName != "") ){
            gotRemove=true;
            break;
        } else {
            continue;
        }
    }
  
    if (gotRemove) {
        printf("The name card is removed\n");
        printf("nameCardID: %d\n", stackOfCards[i].nameCardID);
        printf("personName: %s\n", stackOfCards[i].personName);
        printf("companyName: %s\n", stackOfCards[i].companyName);
        stackOfCards[i].nameCardID = SENTINEL_INT;   
        strcpy(stackOfCards[i].personName,"");
        strcpy(stackOfCards[i].companyName,"");
        strcpy(removeNameCardPersonName,"");
          
    } else {
            for (i=0;i<MAX;i++){
                if (stackOfCards[i].nameCardID != SENTINEL_INT){     //sentinel value
                    isEmpty=false;
                    break;
                }
                else {
                    continue;
                }
            }
      
            if (isEmpty){
                printf("The name card holder is empty\n");
            }
            else {
                printf("The target person name is not in the name card holder\n");
            }
    }
}

void getNameCard(){
    int i=0;
    int j=0;
    char getNameCardPersonName[20]="";
    char comparePersonName[20]="";
    bool gotGet = false;                        
    bool isEmpty = true;
  
    printf("getNameCard():\n");
    printf("Enter personName: \n");
    scanf("\n");                                                                      
    fgets(getNameCardPersonName,20,stdin);
    getNameCardPersonName[strcspn(getNameCardPersonName, "\n")] = 0;  // deletes the \n from stdin
  
  
    while(getNameCardPersonName[i]) {
    getNameCardPersonName[i]=tolower(getNameCardPersonName[i]);
    i++;
    }
  
    for(i=0;i<MAX;i++){
        strcpy(comparePersonName,stackOfCards[i].personName);
        j=0;
        while(comparePersonName[j]) {
        comparePersonName[j]=tolower(comparePersonName[j]);
        j++;
        }
      
        //!strcmp(comparePersonName,getNameCardPersonName) returns 1 if strings match
        if( !strcmp(comparePersonName,getNameCardPersonName) && (getNameCardPersonName != "") ){
            gotGet=true;
            break;
        } else {
            continue;
        }
    }
  
    if (gotGet) {
        printf("The target person name is found\n");
        printf("nameCardID: %d\n", stackOfCards[i].nameCardID);
        printf("personName: %s\n", stackOfCards[i].personName);
        printf("companyName: %s\n", stackOfCards[i].companyName);
      
      
    } else {
            for (i=0;i<MAX;i++){
                if (stackOfCards[i].nameCardID != SENTINEL_INT){     //sentinel value
                    isEmpty=false;
                    break;
                }
                else {
                    continue;
                }
            }
      
            if (isEmpty){
                printf("The name card holder is empty\n");
            }
            else {
                printf("The target person name is not found\n");
            }
    }
}   

void sortNameCards(){
    int i,j;
    int *p = &tempID;

    for (i=0;i<MAX;i++){
        for (int j = i+1; j<MAX; j++){
            if (stackOfCards[i].nameCardID>stackOfCards[j].nameCardID){
                *p=stackOfCards[i].nameCardID;
                strcpy(tempPersonName,stackOfCards[i].personName);     // strcpy uses commas!!
                strcpy(tempCompanyName,stackOfCards[i].companyName);
                stackOfCards[i].nameCardID=stackOfCards[j].nameCardID;
                strcpy(stackOfCards[i].personName,stackOfCards[j].personName);
                strcpy(stackOfCards[i].companyName,stackOfCards[j].companyName);    
                stackOfCards[j].nameCardID=*p;                         // *p seems to be correct
                strcpy(stackOfCards[j].personName,tempPersonName);
                strcpy(stackOfCards[j].companyName,tempCompanyName);
            }
        }
    }
}
