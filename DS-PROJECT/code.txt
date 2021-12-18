#include<stdio.h>
#include<stdlib.h>
#include<ctype.h>
#define N 5

int stack[N];

int top=-1;

void pop() {
    if(top==-1) {
        printf("No data in the register!\n");
        return ; 
    }
    top--;
    return;
}

void push(int n) {
    if(top==N-1) {
        printf("The memory of the register is full!\n");
        return;
    }
    top++;
    stack[top] = n;
    return;
}

void add() {
    int a = stack[top];
    pop();
    int b = stack[top];
    pop();
    push(a+b);
    return;
}

void sub() {
    int a = stack[top];
    pop();
    int b = stack[top];
    pop();
    push(a-b);
    return;
}

void divide() {
    int a = stack[top];
    pop();
    int b = stack[top];
    pop();
    if(a>=b) push(a/b);
    else if(b>a) push(b/a);
}

void mod() {
    int a = stack[top];
    pop();
    int b = stack[top];
    pop();
    push(a%b);
}

void multiply() {
    int a = stack[top];
    pop();
    int b = stack[top];
    pop();
    push(a*b);
}

void display() {
    printf("Current data in the register is:\n");
    for(int i=0;i<=top;i++) {
        printf("%d\t",stack[i]);
    }
    printf("\n");
}

int main(void) {
    int choice,x,a;
    char instr;
    printf("-----------------------------------------------------\n");
    printf("Enter the choices :\n");
    printf("1.Instruction\n2.Display data in register\n3.Exit\n4.insert\n5.delete\n");
    printf(" \nInstructions\n");
    printf(" + - / * ");
    printf("\n----------------------------------------------\n");
    printf("\n");
    printf("Enter data to the register:\n");
    for(int i=0;i<N;i++) {
        scanf("%d",&stack[i]);
    }
    top = N-1;
    while(1) {
    
        printf("Enter choice:\n");
        scanf("%d",&choice);
        switch(choice) {
            case 1: printf("Enter the instruction:\n");
                    scanf(" %c",&instr);
                    switch(instr) {
                    case '+': add(); break;
                    case '-': sub(); break;
                    case '/': divide(); break;
                    case '%': mod(); break;
                    case '*': multiply(); break;
                    }
                    break;
            case 2: display(); 
                    break;
            
            case 3: exit(0); 
                    break;
            case 4: printf("ENter the element\n");
                    scanf("%d",&x);
                    push(x);
                    break;
            case 5: pop();
                    break;
                    
            default: printf("\n Invalid choice\n");
        }
    }
    return 0;
}
