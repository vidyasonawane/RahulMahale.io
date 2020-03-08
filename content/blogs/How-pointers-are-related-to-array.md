+++
date = "2013-08-22"
title = "How pointers are related to array ?"
tags = []
categories = ["technical"]
+++

__Part 1:__

In C and C++ programming language Pointers and Arrays are the hearts of developers. But still much of IT professionals are not familiar with the use of Pointers in C. But pointers and arrays are efficient and a powerful programming practice.  I will try to elaborate a primary use of pointers with arrays, so getting started.

__Pointer__

Pointer is a variable used for addressing; pointer variable also stores the    address of another variable.

Syntax: datatype * variablename; 

Example: int *p;

__Array__

Array is collection of similar type of elements. It stores the elements in contiguous memory locations, Moreover arrays can be one dimensional 2-dimensional and multi-dimensional.

Syntax: datatype variablename[size];

Example: int a[10];

After having known the arrays and pointers basically now we are here to about to cut the cake Pointers and arrays.

__POINTERS AND ARRAYS__

We must have used the arrays and pointers separately in the most of the programming practice. I will focus on using arrays with pointers.

When I say arrays with pointers, technically they can be used in two ways:

1. Pointer to Array and

2. Array of Pointers

__Pointer to Array__

Let us consider the following example:-

int a[10];

int *p;

p =a; //points to the a[0] location.

Above example shows the pointer to an array, here a[10] is an integer type array and p is pointer variable, further a is stored in the p.

Now here a question arises, how can I make a pointer to an array? So that I access the members of the array by using the pointer in a separate function. I’m wondering because I have an array I have to access in functions other than the one it was defined in, but I need it to be defined in that function, and not globally, because the size can depend on the user input. That should let me access the data in other functions right? If so, how do I do that and then access the objects from the pointer?

In above example p= a; points to the a[0]location .

and p= p+1 will point the next location of a[10] that is a[1]

So we can increment and decrement the pointer variable so we can directly access the array elements fast. Also we can scan the array elements by a[i], but assigning array to a pointer a[i] is similar to a+i.

Let us consider a sample example to illustrate it

    int main()
    {
        int a[10],i;
        int *p;
        for(i=0;i<10;i++)
        {
            printf(“enter array elements:- ”)
            scanf(“%d”, a+i); //a+i similar to a[i]
        }
        for(i=0;i<10;i++)
            printf(“array elements are %d”,*(a+i));
        return 0;
    }

Following figure describes the dereferencing with pointer arithmetic:

![pointers](/images/pointers.jpg)
 
Thus in above example we have scanned and printed and array by a+i and *(a+i ) because compiler treats a+i as &a[i] and *(a+i) as a[i]. Moreover we can use this notations in functions and while calling them we can just pass the pointer variable as a parameter or an original variable with the address (&).

Let us consider another example to clear the idea.

    int main()
    {
        int  a[4] = { 1, 2, 3, 4 }, *p, i;
        p = sample(a);
        for (i=0;i<4;i++)
        {
            printf(“%d”, *(p+i));
        }
    return 0;
    }

(int *) sample (int b[ ]) // return-type with pointer is important

    {
        int i;
        for (i=0;i<4;i++)
        b[i]= b[i]+1;
        return (b);
    }

In the above example we have an array of four elements, we are passing that array to function through assigning it to a pointer variable p. this variable stores an address of array a[4], later in function sample we are catching the arrays address in the array variable b[ ].then we are incrementing the b[i] by one and returning it to main( ) and in main ( ) we are just printing the value of a[i] so output is 2, 3, 4, 5.

With above two examples, I hope you might be clear with the pointer to array with one dimensional array.In general we can say that the pointer to array is nothing but storing the base address of the array.