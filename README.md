# C_C++_Advanced
contains all materials and descriptions of the C and C++ advanced course
(https://drive.google.com/drive/folders/1jjzoKAvMiv9q1zVPqWuDF5aCdYt7LtzL?usp=drive_link)

*****************************************************************************************************

## Lesson 7 (Go to):

_ Goto: is a method to change the normal direction of a code to the direction that the coder want.

_ It is needed to have a position label to make the programme move to the desire direction.

    int main()
    {
        char name[20];
        name_position:
        printf("tên là: ");
        scanf("%s",name);
        if(name[0]==NULL)
        {
            goto: name_position;
        }
    }

*****************************************************************************************************

## Lesson 8 (setjum):

_ exit() function helps to end the programme when this function is executed

    if(i==1)
    {
        exit(0) // end the programme
    }
    
_ It is needed to include the _<setjmp.h>_ library to be able to use setjum functions.

_ jmp_buf is a struct type that will be needed to run setjum code.

_ setjmp( jmp_buf ) and longjmp( jmp_buf, int )  are two functions that go together. In detail, when longjmp() are run, the programme will go to the line where the code setjmp is placed.

    jmp_buf jump;
    int i = setjmp(jump);
    printf("i = %d\n", i);
    if(i!=0)
        exit(0);
    longjmp(jump,1); // move to the setjmp() function and its return value will be 1.
    
_ It is applied in button code where there is another button will interrupt when the button is running; and in TRY-CATCH-THROW method to test a code.

*****************************************************************************************************
## Lesson 9 (Pointer):

_ Initialize a pointer: 

    int *ptr1 = NULL;

    float *ptr2 = &a;

    void *ptr = &b;

_ Initialize a pointer in function:

    int sum (int *a, int *b)
    {
        return *a + *b;
    }
_ Function pointer:

    int sum (int *a, int *b)
    {
        return *a + *b;
    }
    
    int product (int *a, int *b)
    {
        return *a * *b;
    }
    
    int calculate (int *a, int *b, int (*ptr) (int,int))
    {
        return ptr(a,b);
    }
    int main()
    {
        calculate(9,6, &sum);
    }
    // The answer will be 15
_ Void pointer:
    
    /*
    It is impossible to point more variable address which have different types. 
    Therefore, void pointer help to point any type of variable, 
    but still need type conversion to get the variable value.
    */
    int main()
    {
        int a;
        float b;
        char c;
        void *ptr = &a;
        ptr = &b;
        ptr = &c;
        // print the value and the address of c variable
        printf("ptr points to value: %d\n ptr storing address: %p", *(char*)ptr, ptr);
    }
_ Type conversion of a function:

    void *ptr = &sum;
    ((int (*)(int, int))ptr)(3,10); // point to sum function
_ Pointer array:
    
    void ptr[] = { &sum, &a, &b };
    printf("%d", *(int *)prt[1]); // print the value of interger variable (a)
_ Pointer of a pointer:
    
    int **ptr2= &ptr1;
    
    
    
*****************************************************************************************************
    
## Lesson 10 (linklist):

_ Work with malloc():

    

_ Create "Node" data type:

    struct Node{
        uint8_t value;
        struct Node* next;
    };
    
    typedef struct Node Node;
    
_ Create createNode() function:

    Node *createNode (uint8_t value)
    {
        Node *newNode = (Node *)malloc(sizeof(Node));
        newNode.value = value;
        newNode.next = NULL;
        return newNode;
    }
_ Create push_back() function:

    void push_back (Node **array, uint8_t value)
    {
        Node *temp, *p;
        temp = createNode(value);
        if(*array == NULL)
        {
            *array = temp;
        }
        else
        {
            p= *array;
            while (p.next !=NULL)
            {
                p = p.next;
            }
            p.next = temp;
        }
    }
