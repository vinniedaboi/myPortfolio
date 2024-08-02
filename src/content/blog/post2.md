---
title: "An Introduction to Algorithms"
description: "Decoding the building blocks of Computer Science"
pubDate: "Nov 21 2023"
heroImage: "https://miro.medium.com/v2/resize:fit:1396/format:webp/1*livRLQMa1lX13Nc5Awfx5A.jpeg"
tags: ["Programming","Algorithms","Computer Science"]
badge: "Informative"
---

# What are algorithms?

The concept of [algorithms](https://en.wikipedia.org/wiki/Algorithm) is relatively simple, algorithms are step-by-step procedures or sets of rules for solving a specific problem or performing a particular task. In computer science, algorithms are the fundamental building blocks of any program. When you try to search for a book in a library using the library system, an algorithm is used behind the computer screen to sort the thousands of books to find the one you want.

![A basic illustration of what an algorithm does](https://miro.medium.com/v2/resize:fit:1320/1*S0rZ6tC4gL4TgaknW1Buzw.jpeg)

Basic Illustration of an algorithm

# Importance of Algorithms

Algorithms are beneficial to us as they make complex/repetitive tasks simple, we can finish said tasks with efficiency and save resources. With the example of the library system, it would take way more time and resources if a librarian were to manually find the book you were looking for instead of having a system that can locate the book using an algorithm. Algorithms are used everywhere you can think of, automobiles, businesses, science, and pretty much anything with technology involved. The stability and systematic approach algorithms provide help us save resources and give us efficiency, well-designed algorithms are crucial in technological advancements and resource utilisation.

![](https://miro.medium.com/v2/resize:fit:1396/1*livRLQMa1lX13Nc5Awfx5A.jpeg)

# Common Algorithm Concepts

Now onto the real deal, sorting algorithms are the most basic and common form of algorithms in computer science both quicksort algorithm and bubble sort algorithm etc organize data systematically while searching algorithms like linear search and binary search efficiently locate specific information within datasets. Space and time complexity is a way of evaluating an algorithm’s performance concerning input size, it allows developers to measure the efficiency of their algorithm to optimise resource and computation speed. I will get into the nitty-gritty of code/math of actual algorithms and time complexity in the next section.

![](https://miro.medium.com/v2/resize:fit:1400/1*07Qu-LznE0umS2Appxjvtw.jpeg)

# Actual Implementation of Algorithms

We are now going to take an actual look into one of the algorithms mentioned earlier — Bubble Sort

Bubble Sort sorts an array of unorganised numbers into numbers from small to big.

Reference the pseudocode, don’t worry if you don’t understand.

Initialize n = Length of Array  
  
BubbleSort(Array, n)  
{  
    for i = 0 to n-2  
    {  
        for j = 0 to n-2  
        {  
            if Array[j] > Array[j+1]  
            {  
                swap(Array[j], Array[j+1])  
            }  
        }  
    }  
}

-   The algorithm starts by comparing the first two elements of the list.
-   If the first element is larger than the second, they are swapped.
-   This process is repeated for each pair of adjacent elements throughout the entire list.

This allows us to end up with a fully sorted array. The code below is the actual implementation of the code in C++, there are two ways to implement it although rather similar I prefer the first version.

#include <iostream>  
  
int main() {  
    // Initialize an array of integers  
    int a[] = {2, 4, 5, 6, 8, 7, 9, 10};  
      
    // Determine the length of the array  
    int length = 8;  
  
    // Outer loop for iterating through each element in the array  
    for (int i = 0; i < length; i++) {  
        // Inner loop for comparing the current element with subsequent elements  
        // The loop starts from the element after the current one (i + 1)  
        // and continues until the second-to-last element  
        for (int j = i + 1; j < length; j++) {  
            // Compare the current element with the subsequent element  
            if (a[i] > a[j]) {  
                // Swap the elements if they are in the wrong order  
                int temp = a[i];  
                a[i] = a[j];  
                a[j] = temp;  
            }  
        }  
    }  
  
    // Output the sorted array  
    for (int i = 0; i < length; i++) {  
        std::cout << a[i] << std::endl;  
    }  
  
    return 0;  
}

#include <iostream>  
  
int main() {  
    // Initialize an array of integers  
    int a[] = {2, 4, 5, 6, 8, 7, 9, 10};  
  
    // Determine the length of the array  
    int length = 8;  
  
    // Outer loop for each pass through the array  
    for (int i = 0; i < length; i++) {  
        // Inner loop for comparing adjacent elements and performing swaps  
        // The loop continues until the second-to-last element  
        for (int j = 0; j < length - 1; j++) {  
            // Compare the current element with the next one  
            if (a[j] > a[j + 1]) {  
                // Swap the elements if they are in the wrong order  
                int temp = a[j];  
                a[j] = a[j + 1];  
                a[j + 1] = temp;  
            }  
        }  
    }  
  
    // Output the sorted array  
    for (int i = 0; i < length; i++) {  
        std::cout << a[i] << std::endl;  
    }  
  
    return 0;  
}

Take this piece of code with a grain of salt if you are a beginner, as long you understand the pseudocode you can implement this in any language. Albeit it would be even better if you did understand the C++ version.

The time complexity of this program will be O(n²) this is because there are two nested loops as well as the fact that the worst-case scenario means the element has to “bubble up” from the start to the end of the array, meaning that the inner loop has to perform n-1 amounts of iterations. But what if I told you there was a method to make bubble sort more efficient?

# Optimisation of Bubble Sort

Optimisations are very crucial when it comes to developing algorithms, without proper optimisation an algorithm can do the opposite and cost resources/efficiency when processing data, programmers do everything they can to make an algorithm as efficient as possible, let’s see how we can do it with bubble sort.

#include <iostream>  
  
int main() {  
    int a[] = {2, 4, 5, 6, 8, 7, 9, 10};  
    int length = 8;  
  
    bool swapped; // Introduce a flag to track whether any swaps occurred  
  
    for (int i = 0; i < length; i++) {  
        swapped = false; // Reset the flag for each pass  
  
        for (int j = 0; j < length - i - 1; j++) {  
            if (a[j] > a[j + 1]) {  
                int temp = a[j];  
                a[j] = a[j + 1];  
                a[j + 1] = temp;  
                swapped = true; // Set the flag if a swap occurs  
            }  
        }  
  
        // If no swaps occurred, the array is already sorted  
        if (!swapped) {  
            break;  
        }  
    }  
  
    for (int i = 0; i < length; i++) {  
        std::cout << a[i] << std::endl;  
    }  
  
    return 0;  
}

Looking at the code above, you can see that I added a swapped flag to ensure that we do not make any unnecessary swaps, even though our algorithm is still O(n²) it is far more efficient as we ensure that we do not pass through any useless swaps to help process larger datasets. In this scenario, this is the best we can do. There are far more complex algorithms that can sort way faster but this is the algorithm I like the most because of its simplicity.

# Conclusion

To sum it up, we’ve covered the basics of what algorithms are, and why they matter, and taken a closer look at Bubble Sort. Now, as you continue your journey into the world of algorithms, remember that they’re not just computer stuff — they’re practical tools for solving all kinds of problems. Feel free to dig deeper, try out different algorithms, and see how they can make things work better. If you’re hungry for more, there are plenty of easy-to-understand resources online to help you become an algorithm pro. So, keep exploring and have fun figuring out how to make computers do cool stuff! Feel free to contact me at vinnie5224@gmail.com if you have any questions.
