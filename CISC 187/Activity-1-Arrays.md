# Activity 1: Arrays
## Question 1: Explain how to create an array of 100 elements. You can choose any data type of your choice. (requires C++ code)
```C++
#include <iostream>

int main() {
    int arr[100];  // array of 100 integers
    return 0;
}
```
## Question 2: What will be the size of each element of an array. (requires C++ code)
```C++
#include <iostream>

int main() {
    int arr[100];
    cout << sizeof(arr[0]) << " bytes" << endl;
    return 0;
}
```
## Question 3: For an array containing 100 elements, provide the number of steps the following operations would take: (theoretical)
* Reading = 1
* Searching for a value not contained within the array = 100
* Insertion at the beginning of the array = 100
* Insertion at the end of the array = 1
* Deletion at the beginning of the array = 99
* Deletion at the end of the array = 1

## Question 4: Normally the search operation in an array looks for the first instance of a given value. But sometimes we may want to look for every instance of a given value. For example, say we want to count how many times the value “apple” is found inside an array. How many steps would it take to find all the “apples”? Give your answer in terms of N. (theoretical)
It will take N (the number of elements in the array) of loops to check for the occurence number of any item. 

## Question 5: Research how to find the memory address of an array. You can use any programming language of your choice. (requires code)
```C++
#include <iostream>

int main() {
    int arr[100];

    cout << "Address of array: " << arr << endl;
    cout << "Address of first element: " << &arr[0] << endl;

    return 0;
}
```
