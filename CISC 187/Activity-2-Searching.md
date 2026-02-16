# Activity 2: Searching
## Question 1: How many steps would it take to perform a linear search for the number 8 in the ordered array, [2, 4, 6, 8, 10, 12, 13]?
To search for 8 in the ordered array [2, 4, 6, 8, 10, 12, 13] using linear search, it will take 4 steps.
First it will compare with 2, then 4, then 6, and then 8. Since 8 matches the required number, it will stop here.

## Question 2: How many steps would binary search take for the previous example? 
To search for 8 in the ordered array [2, 4, 6, 8, 10, 12, 13] using binary search, it will take 1 step.
This is true because middle index of the array is 3, and the value at 3 is 8.

## Question 3: What is the maximum number of steps it would take to perform a binary search on an array of size 100,000?
Maximum number of steps = log2(100,000) ~ 16.6
Therefore, it would take 17 steps to perform a binary search on an array of size 100,000.

## Question 4: Write a C++ program that implements both linear search and binary search algorithms using an array of 100,000 elements. The program should record and report the number of steps (comparisons) performed during each search operation. In addition, analyze and justify the observed behavior by providing a theoretical explanation using Big-O notation, demonstrating why linear search exhibits O(N) complexity and binary search exhibits O(logN) complexity. 
```C++
#include <iostream>
using namespace std;

int linearSearch(int arr[], int size, int key, int &steps) {
    steps = 0;
    for (int i = 0; i < size; i++) {
        steps++;
        if (arr[i] == key)
            return i;
    }
    return -1;
}

int binarySearch(int arr[], int size, int key, int &steps) {
    int left = 0, right = size - 1;
    steps = 0;

    while (left <= right) {
        steps++;
        int mid = (left + right) / 2;

        if (arr[mid] == key)
            return mid;
        else if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}

int main() {
    const int SIZE = 100000;
    int arr[SIZE];

    // Fill sorted array
    for (int i = 0; i < SIZE; i++)
        arr[i] = i;

    int key = 99999;
    int stepsLinear, stepsBinary;

    linearSearch(arr, SIZE, key, stepsLinear);
    binarySearch(arr, SIZE, key, stepsBinary);

    cout << "Linear Search Steps: " << stepsLinear << endl;
    cout << "Binary Search Steps: " << stepsBinary << endl;

    return 0;
}
```
Linear Search is more complex = checks element one by one, steps grow directly with N
Binary Search is quicker = cuts array in half each time, 100,000 --> 50,000 --> 25,000, etc

## Question 5: Write pseudocode for a randomized search algorithm that searches for a given key by randomly selecting indices without repetition. Use a dataset of 100,000 distinct elements, stored in a vector. Each element may be examined at most once during the search. Analyze and state the best-case, average-case, and worst-case time complexities of this algorithm using Big-O notation. Then, implement the algorithm in C++, using only the following standard headers: <vector> for data storage, <random> for random index generation, and <iostream> for input and output. The implementation should track and report the number of comparisons performed during the search. Finally, compare and contrast the randomized search algorithm with linear search and binary search in terms of time complexity, data requirements (such as ordering), and practical efficiency. Discuss scenarios in which each approach may be preferred, highlighting the advantages and limitations of randomized search relative to linear and binary search.
PSEUDOCODE

RandomizedSearch(vector, key):

    Create empty set visited
    comparisons = 0

    While visited size < N:
        Pick random index not in visited
        Add index to visited
        comparisons++

        If vector[index] == key:
            return found, comparisons

    return not found, comparisons


```C++
#include <vector>
#include <random>
#include <iostream>

using namespace std;

int randomizedSearch(vector<int>& data, int key, int& steps) {
    int n = data.size();
    vector<bool> visited(n, false);

    random_device rd;
    mt19937 gen(rd());
    uniform_int_distribution<> dis(0, n - 1);

    steps = 0;
    int visitedCount = 0;

    while (visitedCount < n) {
        int index = dis(gen);

        if (!visited[index]) {
            visited[index] = true;
            visitedCount++;
            steps++;

            if (data[index] == key)
                return index;
        }
    }
    return -1;
}

int main() {
    const int SIZE = 100000;
    vector<int> data;

    for (int i = 0; i < SIZE; i++)
        data.push_back(i);

    int key = 99999;
    int steps;

    randomizedSearch(data, key, steps);

    cout << "Randomized Search Steps: " << steps << endl;

    return 0;
}

```
