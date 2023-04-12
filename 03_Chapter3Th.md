# Chapter 3: The Thrill of Online Convex Optimization

Greetings dear reader! In the last chapter, we delved into the world of competitive analysis and learned how to model and solve problems with multiple adversaries. 

In this chapter, we shall explore the world of online convex optimization (OCO) which has widespread applications in machine learning, game theory and many other fields. 

The OCO problem is one where we are given a sequence of loss functions and our goal is to minimize their sum or average. Unlike a regular optimization problem, we are not given the entire sequence of loss functions beforehand. Instead, the loss functions are revealed to us one at a time, and based on the current loss we must choose a point from a convex set. 

This might seem like a daunting task at first, but do not worry. Our trusty detective, Sherlock Holmes, has come across a case where he needs to solve an OCO problem. He will guide us through the case while we learn the intricacies of online convex optimization.

So fasten your seatbelts and get ready for an exciting journey on the path of OCO with Sherlock Holmes as our companion.
# Chapter 3: The Thrill of Online Convex Optimization

Greetings dear reader! In the last chapter, we delved into the world of competitive analysis and learned how to model and solve problems with multiple adversaries. 

In this chapter, we shall explore the world of online convex optimization (OCO) which has widespread applications in machine learning, game theory and many other fields. 

The OCO problem is one where we are given a sequence of loss functions and our goal is to minimize their sum or average. Unlike a regular optimization problem, we are not given the entire sequence of loss functions beforehand. Instead, the loss functions are revealed to us one at a time, and based on the current loss we must choose a point from a convex set. 

This might seem like a daunting task at first, but do not worry. Our trusty detective, Sherlock Holmes, has come across a case where he needs to solve an OCO problem. He will guide us through the case while we learn the intricacies of online convex optimization.

## The Mystery

Sherlock Holmes and Dr. Watson were called to aid the Royal Mint in London, as they suspected that fake coins were being circulated in the market. The coins were of the highest denomination, and were almost indistinguishable from the genuine ones.

The Mint had been discretely monitoring transactions in the market and had noticed that these fake coins all came from a particular group of merchants. The Mint had already seized some of the coins but did not have enough evidence to arrest the merchants.

Sherlock Holmes was given access to the transaction data that the Mint had collected. The data consisted of a sequence of transactions along with their corresponding profit or loss. 

Holmes quickly realized that the merchants were using a clever strategy. They would set the price for the fake coin slightly lower than the genuine coin, and would sell them to unsuspecting buyers. As a result, the merchants were making a profit on every fake coin sold, and the only way to catch them was to buy the coins at the price they were being sold at.

However, the Mint only had limited resources, and they couldn't afford to purchase all the coins being sold. Holmes had to come up with a clever strategy that would allow them to buy only the coins that were most likely to be fake.

## The Resolution

Sherlock Holmes realized that the problem at hand was an OCO problem. Each transaction was a loss function and his task was to choose which transaction to buy the coin from. Given that the merchants were using the same strategy for each sale, it made sense to model their strategy as a convex set. 

Holmes came up with an algorithm that would minimize the total loss of the purchases made by the Mint. He chose a point from the convex set based on the information he had gathered from previous transactions, and he continued to do so as each new transaction came in.

```python
import numpy as np

class OnlineConvexOptimizer:

    def __init__(self, k, eta):
        self.k = k
        self.eta = eta
        self.weights = np.zeros(k)

    def update(self, x, loss):
        y_hat = np.dot(self.weights, x)
        self.weights -= self.eta * (y_hat - loss) * x / np.linalg.norm(x)

    def predict(self, x):
        return np.dot(self.weights, x)
```

The above code shows a simple implementation of the OCO algorithm that Holmes used. The `update` method updates the current weights based on the current loss, while the `predict` method predicts the next weight to use.

By using this algorithm, Holmes was able to purchase only the coins that were most likely to be fake, and he was able to gather enough evidence to make an arrest. The Mint was very pleased with the outcome, and they commended Holmes on his skill in solving an OCO problem.

And that, dear reader, concludes our journey into the world of OCO with Sherlock Holmes as our guide. We hope that you enjoyed this chapter and learned something new about this fascinating topic. Until next time!
Sure thing! 

The code used in the resolution of the Sherlock Holmes mystery is a simple implementation of the Online Convex Optimization algorithm. Here, we will go through the code and explain how it works:

```python
import numpy as np

class OnlineConvexOptimizer:

    def __init__(self, k, eta):
        self.k = k
        self.eta = eta
        self.weights = np.zeros(k)

    def update(self, x, loss):
        y_hat = np.dot(self.weights, x)
        self.weights -= self.eta * (y_hat - loss) * x / np.linalg.norm(x)

    def predict(self, x):
        return np.dot(self.weights, x)
```

Let's break it down step by step:

1. We start off by importing the `numpy` library, which is a popular library for numerical computation in Python.

2. We define a class `OnlineConvexOptimizer` which is our implementation of the OCO algorithm.

3. Inside the `__init__` method, we define the number of dimensions `k` and the step size `eta`. We also initialize the weight vector `self.weights` with zeros.

4. The `update` method updates the current weight vector based on the current loss. It does this by first calculating the predicted output `y_hat` using the current weight vector and the input vector `x`. It then updates the weight vector by taking a step in the direction of the negative gradient of the loss function at the predicted output. The step size is determined by the `eta` parameter. The gradient is divided by the norm of the input vector to ensure that the step taken is the correct magnitude.

5. The `predict` method predicts the output based on the current weight vector and the input vector `x`. It simply calculates the dot product of the weight vector and the input vector.

In the Sherlock Holmes mystery, we used this algorithm to choose which transactions to buy the coins from based on the current loss function. The input vector `x` was the transaction data, and the loss function was the difference between the actual profit/loss of the transaction and the expected profit/loss of the transaction if the coin was genuine.

Overall, the OCO algorithm is a powerful tool for solving optimization problems, especially in the context of machine learning and data analysis.