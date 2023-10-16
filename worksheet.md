# 03/14 worksheet
## Initial due date: 03/18 @5pm
### Accepted as on time until: 03/20 @11:59pm
Collaborators:

Answer the below questions, and make sure that you commit to your own branch.
When done, run your code through [the autograder](http://autograder.oxy.edu/) and make a pull request on github. Don't forget to tag @irabkina.
Respond to my comments by making new commits to the same branch.

**Be sure to complete the Binary Heaps section of this worksheet *before* starting on P3.**

# Review

1. What makes a trie unique compared to the tree data structures we've discussed so far? *Hint: Think about the organization of data*

2. Why do we need to include terminal nodes in a trie? What would happen if we don't have them?

3. Draw a trie that includes the following words: "tree", "trie", "heap", "heaps", "stack".

4. In your own words, explain what an Abstract Data Type (ADT) is and why they're useful.

5. Methods of ADTs do _not_ have an associated time or memory complexity. Why not?

6. Which ADT is a binary heap a concrete implementation of?  

7. The ADT has two methods that add to and remove/poll from it. What is the relationship between these methods and the percolate up/down functions mentioned in the textbook?

8. What is the "heap property"?

9.     
     a. Given this array of numbers, draw the corresponding (conceptual) binary tree.  

    ```
    {36, 39, 46, 44, 48, 60, 83, 53, 61, 52, 89, 90, 65}
    ```
     b. Given this binary heap, drawn as a rotated (conceptual) binary tree, draw the corresponding array.

    ```
            47
                48
        30
                78
            42
                54
    13
                93
            60
                89
        29
                68
            36
                87
    ```

# Exploration

1.    
    a. What is the breadth (aka branching factor) of a binary trie?  
   b. What is the breadth (aka branching factor) of a trie that uses the English language alphabet (assume 26 characters)?  
c. What is the breadth (aka branching factor) of a trie with an infinitely long alphabet?  
d. What is the worst case time complexity of searching through a trie?  
e. Suppose I had the [Merriam-Webster Dictionary](https://www.merriam-webster.com/) represented as a trie. Explain why, in a practical sense, searching for a word in this dictionary is O(1).

2. The main difference between a trie and a radix tree is that every node of a trie must have exactly one symbol, whereas a radix tree can have entire words as nodes.
    For example, the trie
    ```
         *
         |
         h
        / \
       i   e
      /     \
     *       l
              \
               l
                \
                 o
                  \
                   *
    ```

    can be expressed as the radix tree

    ```
         *
         |
         h
        / \
       i   ello
      /     \
     *       *
    ```

    a. To convert from a trie to a radix tree, any node that is its parent's only child is merged into a single node with the parent. Draw your trie from Review Q6 as a radix tree.  
    b. What is the worst case time complexity of searching for a word in a radix tree? What about the best case?
    c. What is the memory complexity of a radix tree? Assume nodes take up constant space, regardless of the size of the string.
   
3. How is the process of adding a new word to a radix tree different from adding a new word to a trie?

4. For what use cases would you choose a trie over a radix tree? What about a radix tree over a trie?

5. Consider the following min heap:

    ```
        74
    29
            77
        62
            81
    ```

    a. If we were to add 66 to the heap, where would it be placed initially? Draw the resulting binary tree, before any percolating occurs.

    b. We must now percolate up. Which number do we compare 66 with? Do we swap with it? Draw the resulting binary tree.

    c. Continue the heapify process until the heap property is restored. Draw the resulting binary tree.

6. Consider the following min heap:

    ```
            64
        27
            93
    5
                80
            47
                76
        14
                74
            65
                99
    ```

    a. When we `poll()`, what number is returned?

    b. Internally, when `poll()` is first called, the root of the tree is saved to a temporary variable. Which number replaces the root? Draw the resulting binary tree after the root is replaced, before any percolating occurs.

    c. The new root must now be swapped with one of its children. Which one? Why? Draw the resulting binary tree.

    d. Continue the heapify process until the heap property is restored. Draw the resulting binary tree.

# Challenge

1. Radix trees and tries frequently show up in software engineering interviews. In this challenge section, you will answer the following interview-style question:

      > Everything from your favorite IDE to your phone's texting app has autocompletion these days. Implement a class that autocompletes variable names in an IDE. Assume variables are passed in as Strings and all variable names are declared at the time that your class is initialized.    
 
    a. The first step of answering any coding interview question is to talk through the problem to make sure you and your interviewer have the same assumptions. Rephrase the problem here, on a more technical level. What is the interviewer actually asking you to implement?  
   b. Sometimes in coding interviews, you will be given starter code, which you will need to understand. Some code is provided for you in 'Autocompleter.java'. Look at the constructor for the Autocompleter class. What is it doing? How? Make sure to explain what any methods it calls do.  
   c. Coding interviews are often timed. It is always a good idea to start with pseudocode, so your interviewer knows your thought process, even if you run out of time. Write out the pseudocode of your implementation of the `find()` method, which takes a prefix and returns all the variables that start with that prefix. The `main()` method gives some examples of expected behavior. *Hint: It may help to think of `find()` as having two parts: finding the prefix, and outputting the variables that start with it.*  
   d. Coding interviews are often completed on a whiteboard or in Google Docs. *Without using an IDE*, write out the `find()` method for the Autocompleter class.  
   e. Now, copy what you wrote into `Autocompleter.java`. Does your code compile? Does it perform as expected?  
   f. Debug your `Autocompleter.java` implementation until it passes the tests in `main`, taking notes of what you had to fix. What changes did you have to make?   
   g. How does your final implementation differ from the pseudocode?

In questions 2-4 of this section, you will turn your understanding of min heaps into working code. The starter code is provided for you in `MinHeap.java`. You will also need `HeapElement.java` to run it. For this worksheet, a `HeapElement` is just a wrapper around `String`. We do this so you can use your `MinHeap` for Project 3, when the heap will be storing something slightly more complicated.

Before starting, read through the starter file to make sure you understand what is happening. Notice that we have a `Node` class that contains the `HeapElement` and its priority, and that we have a corresponding `Node[] array` member variable. I have also written `resize()` for you, for when the array needs to be doubled. Finally, the `printArray()` and `printTree()` methods will be useful to help you debug your code.

2. Using your answer to Review Q7, complete the `parent()`, `leftChild()`, `rightChild()`, and `swap()` methods.

3. An outline of the `add()` method is in the starter code. The hardest part of `add()` is the percolate up.

    a. There are two cases for when the percolate up should stop. What are they?

    b. Using those two cases as the condition (and'ed together) to a `while` loop, complete the `add()` method.

4. An outline of the `poll()` method is in the starter code. As before, the hardest part of this is the percolate down. Unlike `add()`, we will be using an infinite `while (true)` loop here, and only `break` out of it when necessary. Also notice that we've given you the `currNodeIndex` variable, initially set to 0 (that is, "pointing" to the root).

    a. How would you determine if the current node has children, using the indices of its (potential) children and the size of the heap? Use that to write the code for step 1 of the outline, and `break` out of the loop if the current node has no children.

    b. At this point, we know that the current node has at least one child. For step 2 of the outline, we want to set `childNodeIndex` to refer to the correct child, so that we can compare its priority to the current node. Set `childNodeIndex` based on which child exists (if there is only one child), or the appropriate child if both of them exist.

    c. Compare the child node's priority with that of the current node, and break out of the loop if appropriate.

    d. Finally, `swap()` the current node and the child node, and update `currNodeIndex` appropriately.