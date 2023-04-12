# Chapter 10: Non-stochastic Bandits

Greetings, dear reader! 

In our previous chapter, we explored the fascinating realm of Contextual Bandit Algorithms. We learned about utilizing contextual information to improve our reward predictions and recommendation systems. 

And now, it is time to delve deeper into the world of Bandit Algorithms!

We have the pleasure to introduce you to Peter Auer - a distinguished mathematician and computer scientist known for his extensive research in the field of Multi-armed Bandit problems. 

In this chapter, we will explore Non-stochastic Bandits. These are Bandit Algorithms in which the reward probabilities of the arms do not remain static over time. Instead, they change dynamically and unpredictably. 

Non-stochastic Bandits pose a great challenge to statisticians and computer scientists. Therefore, the ability to solve such problems efficiently is a highly sought-after skill. 

In this chapter, we will cover various algorithms designed to solve Non-stochastic Bandits. We will explore their theoretical foundations, implementation, and evaluate their performance on simulated data. 

We hope you will find this chapter informative, exciting, and mind-bending! 

So fasten your seatbelt and join us on this journey of solving Non-stochastic Bandits!
# Chapter 10: Non-stochastic Bandits - A Sherlock Holmes Mystery

The sun has set, and London is covered in a thick blanket of fog. Detective Sherlock Holmes is sitting in his armchair, lost in thoughts. A knock on the door interrupts his contemplation. It is his dear friend, the mathematician and computer scientist, Peter Auer.
 
"Welcome, Peter! What brings you here?" Sherlock utters as he rises from his chair.
 
Peter seems to be anxious as he explains to Sherlock the reason for his visit. "Sherlock, I am working on a new recommendation system for a client who runs an e-commerce website. I am facing a unique problem. The reward probabilities for some of the items are changing dynamically, and I can't use the usual Bayesian approach to solve it. I fear I will lose the client if I don't come up with a solution soon."
 
Sherlock's interest is piqued. "Interesting. It seems we have a Non-stochastic Bandit problem on our hands. Fear not, Peter. I have just the solution for it."
 
Sherlock Holmes and Peter Auer head off to the client's premises. They collect the data and start working on it. They start by implementing the algorithm that Sherlock came up with. It is a Thompson Sampling algorithm designed to handle Non-stochastic Bandit problems efficiently. 
 
The algorithm works by maintaining posterior distributions of the reward probabilities of each arm. At every iteration, it generates a random draw from each posterior, arm i is selected if the reward of the draw is the highest for that arm. 
 
After working tirelessly for hours, they finally arrive at the solution. They test the algorithm on simulated data, and it performs exceptionally well.
 
Peter is elated at the success of the algorithm. "Sherlock, you are a genius! This algorithm is precisely what I needed. Thank you so much for your help."
 
Sherlock, with a twinkle in his eyes, replies, "Well, Peter, it's not just me. It's the power of Advanced Online Algorithms in Python. With the right tool, anything is possible."

# Resolution

In this chapter, we explored the challenging world of Non-stochastic Bandits. We saw how these problems pose a unique challenge to statisticians and computer scientists. We also had the pleasure of having Peter Auer, a distinguished mathematician and computer scientist, with us. 

We learned about Thompson Sampling, a powerful algorithm designed to handle Non-stochastic Bandit problems efficiently. We discussed its implementation and performance evaluation on simulated data. Through our Sherlock Holmes mystery, we saw the practical implications of the algorithm and how it can be applied in real-world settings.

We hope that you enjoyed this chapter and learned something new. Remember, with Advanced Online Algorithms in Python, you can solve even the most challenging problems.
In the Sherlock Holmes mystery, we explored Non-stochastic Bandit problems and solved it using Thompson Sampling algorithm. In this section, we will delve deeper into how Thompson Sampling algorithm works and its implementation in Python.

## Thompson Sampling Algorithm

Thompson Sampling is a Bayesian algorithm that solves Non-stochastic Bandit problems efficiently. It maintains posterior distributions of the reward probabilities of each arm. At every iteration, the algorithm generates a random draw from each posterior, arm i is selected if the reward of the draw is the highest for that arm.

The following steps summarize the Thompson Sampling algorithm:

1. Initialize the prior distribution for all arms.
2. Choose an arm i based on its prior distribution.
3. Observe the reward of arm i.
4. Update the posterior distribution for arm i.
5. Repeat steps 2 to 4 until the stopping criterion is met.

## Implementation in Python

Let's implement Thompson Sampling algorithm in Python for a Non-stochastic Bandit problem. We'll simulate a dataset of three arms with varying reward probabilities.

```python
import numpy as np

# Define the number of arms and rounds.
num_arms = 3
num_rounds = 1000

# Define the true reward probabilities for each arm.
true_probs = np.array([0.1, 0.3, 0.5])

# Define the prior beta distribution for each arm.
prior_params = np.ones((2, num_arms))

# Initialize the reward and number of times each arm is selected.
rewards = np.zeros(num_arms)
num_selections = np.zeros(num_arms)

# Define the Thompson Sampling function.
def thompson_sampling(prior_params, num_arms):
    theta = np.zeros(num_arms)
    for i in range(num_arms):
        theta[i] = np.random.beta(prior_params[0][i], prior_params[1][i])
    return np.argmax(theta)

# Run the Thompson Sampling algorithm.
for t in range(num_rounds):
    # Choose the arm to play based on the prior.
    arm = thompson_sampling(prior_params, num_arms)
    # Update the reward and number of times the arm is selected.
    reward = np.random.binomial(1, true_probs[arm])
    rewards[arm] += reward
    num_selections[arm] += 1
    # Update the posterior.
    prior_params[0][arm] += reward
    prior_params[1][arm] += 1 - reward
```

In the code above, we initialized the number of arms and rounds. We defined the true reward probabilities for each arm and prior beta distribution for each arm. Then we implemented the Thompson Sampling function which generated a random draw from each posterior distribution and returns the chosen arm. We ran the Thompson Sampling algorithm for 1000 rounds and updated the reward, number of times each arm is selected, and the posterior distribution.

Once we have the estimated reward probabilities for each arm, we can use them to recommend the best arm for the next round.

Thompson Sampling is a powerful algorithm that solves Non-stochastic Bandit problems efficiently. It is easy to implement and perform well in practice. With the right tools and approaches, Non-stochastic Bandit problems can be solved with ease.