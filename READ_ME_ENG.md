This program is in the C# programming language,
perform array sorting using the pyramid sorting algorithm,
mass conversion into a primary pyramidal pile or into a binary village,
where the main element is the choice of the smallest element of the array at the top of the compound pyramid;
compound pyramid.
This method has a proven minimum performance and
thus, when sorting huge arrays more than 1000 elements are available

The main module Sorting Piramide contains the main function:
the main task is to create an array for sorting, filling it with random number,
array method add2pyramid, showing array elements before sorting,
Pyramid_Sort.

Methods with which the main function works:
1) an algorithm for converting an array to a primary pyramidal heap or binary tree
add2pyramid - converts an array into a primary pyramidal heap or into a binary village
the bulk, where smaller elements of the array are placed in the right side of the pyramidal heap
large elements are placed on the left side of the first element,
the smallest element is placed on top of the pyramidal heap.
After conversion to the Pyramid_Sort method;
2) an algorithm for building pyramids from a pyramid mass and sorting a pyramidal array
Pyramid_Sort - builds a pyramid pile from a pyramid sifting it from the bottom level,
Data that takes from the add2pyramid attribute and sorts the pyramid array
The data on the sorted array is passed to the main function main.