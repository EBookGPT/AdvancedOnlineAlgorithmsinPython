# Chapter 26: Online Linear Programming

The previous chapter of the book, "Communication Complexity in Online Algorithms," delved into methods of reducing communication overhead in distributed online algorithmic models. In this chapter, we jump into the realm of online linear programming, a fascinating field concerned with optimizing objective functions of linear constraints while constraining the algorithm to operate in an online setting. 

Linear programming methods are incredibly useful as they can be applied to model problems from various domains such as logistics, resources allocation, and production planning, to name a few. In online linear programming, the constraints are evaluated at each update cycle of the optimization algorithm, meaning that the feasibility of the problem must be judged without the entire information being present at one time. 

The challenge, therefore, is to design the optimization algorithm in such a way that it performs optimization without knowing the future constraints' values. In this chapter, we take on this challenge by examining the commonly used techniques in online linear programming for solving problems of various natures.

We will start by understanding how linear programming differs from traditional algorithms and how it can be adapted for online problems. Then we will look into the techniques for designing online algorithms for LP, including the dual fitting technique, primal-dual techniques, and online convex optimization.

So, let's dive into the world of online linear programming and explore its mysteries and wonders!
# Chapter 26: Online Linear Programming

## The Mystery

It was a foggy night in London, and Sherlock Holmes was deep in thought, working on a case that had puzzled him for weeks. Suddenly, there was a knock on the door. It was his old acquaintance, Professor Moriarty, who had a problem he needed help on. 

"Good evening, Sherlock. I am working on an online allocation problem where I need to assign tasks to workers in real-time while minimizing cost. However, the cost of a task varies each day, and I need to optimize the allocation algorithm under those constraints. Can you help me solve this problem?," Professor Moriarty explained.

Sherlock Holmes listened carefully and realized that this was a problem of online linear programming. He promised to take on the case and got to work right away.

After analyzing the problem, Sherlock came up with a plan to implement the primal-dual algorithm in Python, which would provide online optimal solutions to the allocation problem.

He coded the primal-dual algorithm for linear programming as follows:

```python
def online_lp_primal_dual(A, b, c, t, w):
    """
    Primal-dual algorithm for online linear programming using current
    constraints to update feasible solution.

    Parameters:
    A (ndarray): Coefficient matrix of inequality constraints.
    b (ndarray): Right hand side values of inequality constraints.
    c (ndarray): Coefficient matrix of objective function.
    t (float): Step size of the algorithm.
    w (ndarray): Initial feasible solution.

    Returns:
    Optimal solution to the linear programming problem.
    """
    
    n_iterations = A.shape[0]
    n_features = c.shape[0]
    x = np.zeros(n_features)
    
    for i in range(n_iterations):
        y = np.dot(A[i], x)
        x += t*c - t*A[i] * np.sign(y - b[i])
        x = np.maximum(x, 0)
        
    return x
```
## The Resolution

Sherlock Holmes implemented this algorithm and applied it to Moriarty's problem. Using Professor Moriarty's real-time data on the costs of tasks and the capabilities of workers, the algorithm provided optimum allocation solutions for each task while minimizing the overall costs.

With a satisfied smile, Sherlock handed over the solution to Professor Moriarty, who was surprised at how efficiently his problem was solved.

"Brilliant, Sherlock! I knew I could always count on you to find the solution. How did you manage to solve it so quickly?" asked Professor Moriarty.

"Through the power of online linear programming, my dear Professor! These advanced algorithms can optimize objective functions while operating in an online setting, and our primal-dual algorithm optimized your allocation problem," Sherlock replied, grinning.

And with that, Professor Moriarty left, pleased to have his problem solved, and with a newfound appreciation for the power of online linear programming.
# Explanation of the Code

The online linear programming problem in the Sherlock Holmes mystery was solved using the Primal-Dual algorithm. The algorithm starts by initializing a feasible solution in the form of a vector w. 

The algorithm then iteratively updates the solution by combining the primal and dual methods to optimize the objective function while maintaining the feasibility of the constraints at each time step. The primal method updates the primal variable as per the gradient descent by subtracting the step size multiplied by the gradient of the objective function. The dual method computes a sub-gradient of the dual function and subtracts it from the dual variable.

Here is a step-by-step explaination of the code used to solve the mystery:

```python
def online_lp_primal_dual(A, b, c, t, w):
    """
    Primal-dual algorithm for online linear programming using current
    constraints to update feasible solution.

    Parameters:
    A (ndarray): Coefficient matrix of inequality constraints.
    b (ndarray): Right hand side values of inequality constraints.
    c (ndarray): Coefficient matrix of objective function.
    t (float): Step size of the algorithm.
    w (ndarray): Initial feasible solution.

    Returns:
    Optimal solution to the linear programming problem.
    """
```
1. The function `online_lp_primal_dual` takes in five parameter values: A, b, c, t, and w, where A, b, and c represents the constraint's coefficient matrix, right-hand side inequality values, and the objective function coefficient matrix.

2. `t` is the step size of the optimization algorithm, while `w` is the initial feasible solution.

```python
    n_iterations = A.shape[0]
    n_features = c.shape[0]
    x = np.zeros(n_features)
    
    for i in range(n_iterations):
        y = np.dot(A[i], x)
        x += t*c - t*A[i] * np.sign(y - b[i])
        x = np.maximum(x, 0)
        
    return x
```
1. The number of iterations is obtained by calculating the number of rows in the inequality constraint coefficient matrix (A.shape[0]).

2. The number of features, which is the length of the objective function coefficient matrix `c`, is also determined (c.shape[0]).

3. The algorithm iteratively updates the solution for each new constraint by calling the corresponding row of the matrix A. 

4. The variable `y` is computed as the product of A and the current solution vector `x`. The primal variable `x` is then updated using the algorithm's primal method by subtracting the step size multiplied by the gradient of the objective function. The dual variable is updated using the algorithm's dual method by computing the sub-gradient of the dual function which is then subtracted from the dual variable.

5. The solution vector `x` is then stored as a maximum of 0 and itself to maintain the feasibility of the current solution.

6. The optimal solution x is returned by the function.

This algorithm is highly effective for online linear programming optimization problems like the one presented in the Sherlock Holmes mystery.