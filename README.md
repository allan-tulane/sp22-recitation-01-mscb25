# CMPS 2200  Recitation 01

**Name (Team Member 1):**__Maddie Bonanno___________  
**Name (Team Member 2):**____Riley Martin______________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [done] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [done] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [done] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [done] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**The worst case input key for linear_search is the final value of the list; in the test cases, this value is 5. The worst case input key for binary_search is the element on one of the ends (left or right), as it requires maximum comparisons; in the test cases, this value is 1 or 5**

- [done] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**The best case input key for linear_search is the first value of the list; in the test cases, this value is 1. The best case input for binary_search is the mid value; in the test cases, this value is 3**

- [done] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [done] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [done] 8. Call `print_results(compare_search())` and paste the results here:

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.007 |    0.009 |
|      100.000 |    0.018 |    0.027 |
|     1000.000 |    0.215 |    0.012 |
|    10000.000 |    2.482 |    0.025 |
|   100000.000 |   32.330 |    0.031 |
|  1000000.000 |  490.536 |    0.041 |
| 10000000.000 | 4839.699 |    0.042 |

- [done] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**yes, they do match empirical results because binary search is significantly faster as the value of n increases** 

- [done] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **the worse case complexity will be n^k - the list doesn't have to be sorted**
  + For binary search? **logn^k - has to be sorted first**
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **for all values of k > 2**

