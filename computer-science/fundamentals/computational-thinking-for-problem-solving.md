---
description: >-
  Notes from
  https://www.coursera.org/learn/computational-thinking-problem-solving
---

# Computational thinking for problem solving

## Week 1

Four pillars of computational thinking:

* **Decomposition:** Breaking a complex problem into more manageable sub-problems.
* **Pattern recognition:** Finding similarities or shared characteristics within or between problems.
* **Data representation and abstraction:** Determining what characteristics of the problem are important and filtering out those that are not.
* **Algorithms:** Step-by-step instructions on how to solve a problem. Flowcharts or pseudocode.

### Assignment Week 1

**Problem:** Count the number of occurrences of a word and its synonyms in a corpus of text documents.

* Decomposition
  1. Get a list with the synonyms of the keyword
  2. Look for each one of the words on the list on the Corpus
* Pattern recognition
  * The process to be repeated: Look for each one of the words on the list on the Corpus
* Data representation and abstraction
  * Inputs: Keyword, Thesaurus (synonyms) and Corpus (set of documents)
  * Output: Number of occurrences of the keyword and its synonyms in all the documents in the corpus.
  * Out of scope: Capitalization, partial word matching, punctuation, alternate spellings, word variations.
* Algorithms:
  1. Get a list with the synonyms of the keyword
  2. Look for each one of the words on the list on the Corpus
  3. Repeat until done

## Week 2

**Find-Max:** Iterate through each item in the list and compare with the current Max. O(N)\
**Linear search:** Look at each value in the list, if it's equal, stop. O(N)\
**Binary search:** Sorted list. Start the search in the middle of the list, iterate comparing with the searched item, remove the middle elements and half the list that are larger or smaller depending on the case, and repeat.  O(LogN)\
**Brute force algorithms:** Can be used for solving optimization problems. Check all possible options. Combinations or permutations (if order matters). O(exponential) or O(factorial).\
**Greedy algorithms:** Locally optimal for optimization problems.

**Algorithmic complexity:** Worst-case scenario.

## Week 3

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>von Neumann architecture</p></figcaption></figure>

Collections, objects, variables, conditionals, loops, pseudocode.

### **Control unit operations:**

* **Fetch:** Read the instruction from memory
* **Decode:** Figure out what it means and put operands in the right place
* **Execute:** Perform the instruction and put the results in the right place
* **Update:** Set the address of the next instruction to execute

## Week 4

**Python:** Variables, conditional statements, lists, iterations (for-loop, for-loop using ranges, while-loop), functions, classes, objects.
