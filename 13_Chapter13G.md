# Chapter 13: Geometric Online Convex Optimization

Welcome, dear reader, to the 13th chapter of our book on Advanced Online Algorithms in Python. In this chapter, we dive into the world of geometric online convex optimization (OCO) and explore its applications in various fields.

As the algorithms become more complex, we need a detective to guide us in the right direction. Therefore, it is our pleasure to announce that we'll have a special guest in this chapter. None other than Stephen Boyd himself, an American engineer, and professor at Stanford University. He is well-known for his work on geometric OCO, among other areas of optimization.

This chapter presents an extension of online convex optimization to the setting of the geometry optimisation problem. In the traditional formulation of OCO, the goal is to minimize the sum of convex losses over a set of rounds. In geometric OCO, we instead study another different class of the objective function constructed based on the geometry of the problem where we not only want to minimize the function but also any function of its gradient.

We proceed to introduce the most popular geometric OCO problem of linear optimisation in a specialized n-dimensional space. Further, we learn about the stochastic and online mirror descent algorithms for solving these problems. The chapter concludes with practical applications of geometric OCO and an analysis of their efficiencies.

So, let's begin the adventure and unravel the mysteries of geometric OCO with Sherlock Holmes and Stephen Boyd.
# Chapter 13: Geometric Online Convex Optimization

Welcome, dear reader, to the 13th chapter of our book on Advanced Online Algorithms in Python. In this chapter, we will join the great detective Sherlock Holmes and his friend Dr. Watson to solve a mystery involving geometric online convex optimization.

Holmes and Watson were enjoying their evening with a game of chess when they heard a knock at their door. Upon opening, they found a well-dressed gentleman standing outside.

"Good evening, gentlemen. My name is Lord Cedric and I am in dire need of your assistance. I work at a financial firm and we have been experiencing significant losses in our investment portfolio. I believe the problem lies in our optimization algorithm, but I can't quite put my finger on what's wrong," said Lord Cedric.

Holmes, intrigued by the case, asked Lord Cedric to explain the specifics. After hearing the details, Holmes realized that the optimization algorithm they were using was a classic case of geometric online convex optimization gone awry.

With the help of Dr. Watson and Stephen Boyd, who was conveniently in town for a conference, Holmes set out to solve the mystery. They began by carefully studying the algorithm that Lord Cedric's firm was using and discovering that it was unable to adapt to the changing market trends.

Next, Stephen Boyd introduced them to the stochastic gradient descent and online mirror descent algorithms, which were specifically designed for geometric OCO problems. Applying these algorithms to the case at hand, they were almost immediately able to identify the faults in the original algorithm and correct them.

After meticulous analysis and testing, Holmes and his team were able to get Lord Cedric's firm back on track, and his financial portfolio was no longer suffering losses. Lord Cedric was thrilled with the team's success and thanked them profusely.

With the case solved, Holmes and Watson bid adieu to Stephen Boyd and Lord Cedric, with a sense of satisfaction knowing that they had once again used their detective skills to help those in need.

In conclusion, geometric online convex optimization is a powerful tool that can be used to solve complex problems in various fields. With the help of experts like Stephen Boyd and careful analysis of algorithms, we can solve the mystery of optimization and achieve great success.
The Sherlock Holmes mystery in Chapter 13 required the implementation of stochastic gradient descent and online mirror descent algorithms to solve a geometric online convex optimization problem. Here, we will briefly explain the code used to solve the mystery.

### Stochastic Gradient Descent 

Stochastic Gradient Descent is an optimization algorithm that uses randomization to solve optimization problems faster. In geometric online convex optimization, it is a powerful tool that can be applied to find optimal solutions for many problems. The implementation of the algorithm in Python can be done as follows:

```python
def stochastic_gradient_descent(x_init, grad_fn, step_size, num_iterations):
    x = x_init
    for i in range(num_iterations):
        grad = grad_fn(x)
        x = x - step_size * grad
    return x
```

Here, `x_init` represents the initial point of the algorithm, `grad_fn` is the function that computes the gradient at point `x`, `step_size` is the step size for each iteration of the algorithm, and `num_iterations` is the total number of iterations to perform.

### Online Mirror Descent

Online Mirror Descent is a convex optimization algorithm that is frequently used in online learning problems. In geometric online convex optimization, it can be applied to solve a number of problems. The implementation of the algorithm in Python can be done as follows:

```python
def online_mirror_descent(x_init, grad_fn, cost_fn, step_size, num_iterations):
    x = x_init
    y = np.zeros(x_init.shape)
    for i in range(num_iterations):
        grad = grad_fn(y)
        x = (1 - step_size) * x + step_size * grad / np.linalg.norm(grad)
        y = y - step_size * cost_fn(x)
    return x
```

Here, `x_init` is the initial point of the algorithm, `grad_fn` returns the gradient of the convex function being optimized, while `cost_fn` returns the cost of the function at point `x`, `step_size` is the learning rate, and `num_iterations` is the total number of iterations to be performed.

Finally, it is important to note that these algorithms are just some of the many tools available to solve geometric online convex optimization problems. The suitability of each algorithm depends on the specific problem being solved, and expert advice should be sought in case of complex problems.