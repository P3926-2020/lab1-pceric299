# Lab 1: Python intro

## Skills: elementary programming with loops and conditionals, scripts, basic plotting

### Background

One of the easiest to formulate, yet unsolved, problems in number theory is the Collatz Conjecture, sometimes called the “Hailstone Problem.” Given a starting integer _n, n >= 1_, we iterate the following sequence:
* _n --> (n/2)_ if _n_ is even
* _n --> (3n+1)_ if _n_ is odd

The Collatz Conjecture is that for any _n_, this iterative sequence will end in 1 after a finite number of steps. This conjecture has defied all attempts at proof.

Let’s try an example. If you start with _n = 5_, you generate the sequence 16, 8, 4, 2, 1. Let’s use the notation _C(5) = 5_ where _C( )_ represents the iterative sequence above; therefore, _C(n)_ returns the number of iterations required to reach 1 starting with the number _n_. Similarly, _C(7) = 16_, and the sequence is
22, 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1. This is called the “Hailstone Problem” because it is usually the case that the numbers rise above _n_, and then fall and rise a number of times before reaching 1. Note that _C(1) = 3_ and this generates the sequence 4, 2, 1. 

For this reason, the Collatz Conjecture is really that _C(n)_ for all _n_ results in the infinite cycle 1, 4, 2, 1, 4, 2, 1, . . .. The conjecture explicitly excludes the following behaviour: 
(1) any integer resulting in a sequence that goes off to infinity, and 
(2) any integer resulting in an attracting sequence other than 1, 4, 2, 1, . . ..

The Collatz conjecture has been checked for all _n_ up to about 2e18 and all go to 1. It’s both famous and infamous: famous because it’s a simple problem that defies solution, and infamous because it does not seem connected with any deeper ideas in number theory. The latter is the origin of the following joke: “Mathematicians at Harvard became aware of the Collatz Conjecture and worked on it for about a month with no results. Then, mathematicians at Princeton found out about it and worked on it for another month with no results, and so on and so on. The real purpose of the Collatz conjecture is to slow down mathematical research in the US.”



### Part 1
Write a script, `collatz_single.py`, to implement the iterative sequence above for an integer _n_ read from the keyboard. The iterative sequence should be printed to the screen, stop when 1 is reached, and print the number of iterations needed to reach one, i.e. _C(n)_.

### Part 2
Write another script, `collatz_multiple.py`, to compute _C(n)_ for all integers up to one million. In this case, it is probably not wise (except when you are checking your routine) to print the sequence for each _n_. 

Your script should determine the integer which had the maximum number of iterations to reach 1 and should produce a (nice looking) plot of _C(n)_ versus log<sub>10</sub>(_n_). (Check: what is the default base for logarithms in `numpy`?) Save the figure to a file and add it to your repository. The code that makes the plot should be included in the `collatz_multiple.py` file.

Finally, time how long your script takes to finish. Hint: one simple method is the Python `time` module. You can do 

```
starttime = time.time() 

<your code here>
    
endtime = time.time()

elapsed = endtime-starttime
```

### Part 3
Potential Speedup: As _(3n+1)_ must be even for any odd _n_, the two rules can be combined into one in this case: any odd _n_ should iterate to _(3n + 1)/2_. Create a new script `collatz_multiple2.py` that implements this modification. Be sure to count the _(3n+1)/2_ step as two iterations in order to reproduce your previous results. How much faster is your new routine? The code that computes this speed-up factor should be included in the `collatz_multiple2.py` file.
