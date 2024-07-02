# Tom Tutone T2A1-A Workbook Part A

* Remember to export md files to pdf in Windows not WSL
* Both qs are marked in three parts:
    1. Provides a full and clear explanation for all algorithms, showcasing exceptional understanding in each explanation.
    2. Provides clear explanations for all four algorithms, describing how the Big O notation numbers were calculated. Demonstrates an excellent understanding of the relationship between algorithmic structures and Big O complexity.
    3. Provides a comprehensive evaluation of algorithm efficiency using Big O notation. Explicitly compares the two algorithms in each pair and considers their practical applicability. Provides insightful discussions on edge cases. Demonstrates a high-level understanding of the implications of time complexity in practical use cases.

## Q1. Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O), min 300 words /2 /2 /2

* bubble sort
* merge sort

Two common types of sorting algorithms are the bubble sort and merge sort methods.

The bubble sort method works by taking one value from a set and comparing it to each other value in the set, from left to right. If the considered value is larger than a value it is compared against, the two values switch places. If not, the values do not swap places. This process continues until all values have been compared against the considered value. The next value in the original set is then considered and compared against every value. Once every value has been considered, the list is sorted from smallest to largest.

Bubble sorting is infamously an inefficient sorting method because the sorting method does not draw logical conclusions and must make evaluations that are unneccesary. For example, the smallest value in an array will still be compared to every other value. Coded, bubble sort will feature a loop which iterates through the input set to consider each value then a nested loop iterating through the set again to compare the considered value against each value. Because each value in a set must be considered completely, the Big O notation for a bubble sort is O(_n_^2) where _n_ is the number of values in the input set.

Merge sort is an alternative sorting method that is more complex to program but more efficient. A merge sort first continually halves a set until it is fractioned into single values. The singular fractions are then paired up, compared and the smaller value is placed on the left creating a new, combined fraction. The function then pairs up these new fractions and begins comparing them. At this next comparison step, the first index in each fraction is compared. Whichever value is smaller is recorded in an output list and the next value from its fraction is then compared against the value that was not added to the output list. This process continues until one there are no more values to compare on one side and the remaining, largest value is added to the output fraction at its right-most end. This process of merging fractions and comparing their indexes continues until the original set has been reassembled, now, completely sorted.

Dividing a set of values takes a set amount of time so this step is disregarded in terms of Big O notation. Once the set's values are completely divided into single values, the sorting method is called for each fraction. The number of fractions there are is relative to the number of times the original set was initially halved, which can be expressed as $log{_2}{n}$/. The merging step requires considering each value, a Big O complexity of _n_. The sorting method is called for each merge meaning a Big O notation of n$log{_2}{n}$/ (Khan Academy, n.d.).

In terms of complexity, bubble sort and merge sort have different strengths. Bubble sort is advantageous because it is easy to program and can function quickly with small sets of values. However, as the number of values to be analysed increases, the complexity rapidly scales, a significant disavantage. Alternatively, merge sort requires thoughtful programming and, because it has a logarithmic complexity, requires a relatively high amount of computing to initially function. Merge sort is significantly more efficient as the number of values being sorted increases, a distinct advantage when dealing with large datasets. This tipping point of efficiency comes quickly and, in most cases, merge sort should be the preferred sorting method.

### References

Khan Academy (n.d.) _[Analysis of Merge Sort](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/analysis-of-merge-sort)_, mKhan Academy Website, accessed 2 July 2024.

## Q2. Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O) /2 /2 /2

* binary search
* linear search
