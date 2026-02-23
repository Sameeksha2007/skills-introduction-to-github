# Activity 3: Sorting Algorithms
## Question 1: Use Big O Notation to describe the time complexity of an algorithm that takes 4N + 16steps.
The constants are ignored; therefore, 4N becomes N, and the 16 is ignored.

Final Answer = O(N)

## Question 2: Use Big O Notation to describe the time complexity of an algorithm that takes 2N^2. 
The constant 2 is ignored.

The highest power of N is the most important part.

Final Answer = O(N^2)

## Question 3: Use Big O Notation to describe the time complexity of the following function, which returns the sum of all numbers of an array after the numbers have been doubled:
```C++
def double_then_sum(array) 
	doubled_array = []

	array.each do |number| 
		doubled_array << number *= 2
	end

	sum = 0

	doubled_array.each do |number| 
		sum += number
	end
	return sum 
end
```

The overall thing is that the function doubles every number and then sums everything together. 

The first lopp goes through the array once and then the second loop goes through the array once.

Both of these follow O(N); therefore, O(N) + O(N) = 2O(N), and since the constant is dropped, the final answer is O(N).

## Question 4: Use Big O Notation to describe the time complexity of the following function, which accepts an array of strings and prints each string in multiple cases: 
```C++
def multiple_cases(array) 
	array.each do |string|
		puts string.upcase 
		puts string.downcase 
		puts string.capitalize
	end 
end
```
For each string, the code prints the upcase, downcase, and capitalize; therefore, each string does 3 operations.

Number of Strings = N --> N * 3 operations --> O(N)

## Question 5:The next function iterates over an array of numbers, and for each number whose index is even, it prints the sum of that number plus every number in the array. What is this function’s efficiency in terms of Big O Notation?
```C++
def every_other(array) 
	array.each_with_index do |number, index|
		if index.even?
			array.each do |other_number|
            	puts number + other_number
			end 
		end
	end 
end
```
The code has two loops and each loop goes through O(N) once.

Outer Loop {O(N)} * Inner Loop {O(N)} = N * N = O(N^2)
