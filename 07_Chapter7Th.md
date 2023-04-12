# Chapter 7: The Mysterious Case of the Multi-Armed Bandit

Welcome back dear readers! In our last chapter, we explored the delicate balance between exploitation and exploration in online algorithms. But what happens when we have limited resources and must make decisions based on incomplete information? Enter the Multi-Armed Bandit problem.

In this chapter, we will take a deep dive into the world of Multi-Armed Bandit algorithms. We will follow Sherlock Holmes and Dr. Watson as they assist our special guest investigator, Peter Auer, in solving a perplexing case where our limited resources are the only means of solving a heinous crime.

So sit back, and allow us to transport you to the world of Multi-Armed Bandit algorithms where we will learn about different strategies such as Epsilon Greedy, UCB1, and Thompson Sampling. We will implement each of these strategies in Python and see how they perform on our mystery case.

So without further ado, let us join our esteemed guests on their investigation and discover the power of Multi-Armed Bandit algorithms!
# Chapter 7: The Mysterious Case of the Multi-Armed Bandit

Sherlock Holmes and Dr. Watson were settled in their sitting room, discussing the latest mystery they had been asked to solve. Suddenly, there was a knock on the door. It was their old friend and famed investigator, Peter Auer. He had come with a perplexing case that had stumped even him.

The case involved a serial arsonist who had been burning down houses in a small town. Despite their best efforts, the police had been unable to apprehend the arsonist, and the town was living in fear.

The only lead the investigators had was a witness who claimed to have seen a suspicious figure lurking near one of the burnt-down houses. The figure was dressed in a blue hoodie and had a backpack on. The witness was unable to give any more details, and the investigators were left with limited resources to solve the case.

This is where Multi-Armed Bandit algorithms came into play. The investigators realized that they had to make decisions based on incomplete information. They had to decide which houses to watch, which neighborhoods to patrol and which suspects to investigate first. The only way to do this was to use Multi-Armed Bandit algorithms.

First, they tried the Epsilon Greedy algorithm. This algorithm is simple to implement and balances exploration and exploitation based on a variable epsilon. Using this algorithm, the investigators watched a random set of houses, patrolled a few areas, and questioned a few suspects. Although this algorithm was effective, the investigators soon realized that they were not maximizing their resources.

Next, they tried the UCB1 algorithm. This algorithm accounts for both the number of times an arm has been played and the average reward obtained so far. This algorithm proved to be more effective than the Epsilon Greedy algorithm. The investigators were able to zero in on specific suspects and neighborhoods, resulting in the identification and eventual capture of the arsonist.

Just when the investigators thought they had solved the case, a new twist presented itself. It turned out that the witness had only seen the suspicious figure in a blue hoodie in one instance. The investigators were left with only a single data point to make their decision, making the case even harder to solve.

This is where Thompson Sampling came in. This algorithm takes into account the probability distribution of the reward function of each arm. Using this algorithm, the investigators were able to update their beliefs after every data point and make decisions accordingly. This algorithm proved to be the most effective, and the investigators were finally able to solve the case.

Thanks to the power of Multi-Armed Bandit algorithms, the investigators were able to apprehend the arsonist and bring peace back to the small town. The Epsilon Greedy, UCB1, and Thompson Sampling algorithms were all key in solving this perplexing case.

We hope this mystery has helped you understand the true power of Multi-Armed Bandit algorithms. Until next time, dear readers!
# The Code Behind the Mysterious Case of the Multi-Armed Bandit

To solve the case, the investigators used three different Multi-Armed Bandit algorithms: Epsilon Greedy, UCB1, and Thompson Sampling. Let's take a closer look at the code used to implement each of these algorithms in Python.

## Epsilon Greedy Algorithm

The Epsilon Greedy algorithm is one of the simplest Multi-Armed Bandit algorithms, and it balances exploration and exploitation based on a variable epsilon. Here is the Python code implementing the Epsilon Greedy algorithm:

```python
import random

def epsilon_greedy(arms, epsilon):
    """Epsilon Greedy algorithm for Multi-Armed Bandit problem."""
    num_explorations = int(len(arms) * epsilon)
    num_exploitations = len(arms) - num_explorations
    
    rewards = [0] * len(arms)  # rewards for each arm
    plays = [0] * len(arms)  # number of times each arm is played
    total_reward = 0
    
    # Exploration
    for i in range(num_explorations):
        arm = random.randrange(0, len(arms))
        reward = arms[arm].pull()
        rewards[arm] += reward
        plays[arm] += 1
        total_reward += reward
    
    # Exploitation
    for i in range(num_exploitations):
        arm = rewards.index(max(rewards))
        reward = arms[arm].pull()
        rewards[arm] += reward
        plays[arm] += 1
        total_reward += reward
    
    return total_reward
```

In this code, `arms` is a list of Bandit objects representing each arm of the Multi-Armed Bandit. The `pull()` method of the Bandit object returns a binary reward (1 or 0) from pulling that arm. `epsilon` is the degree of exploration, ranging from 0 (pure exploitation) to 1 (pure exploration).

The algorithm starts with exploration, where a random arm is chosen and pulled. The reward is recorded, and the count of that arm's plays is incremented. This continues for a certain number of explorations determined by `epsilon`. After exploration, the algorithm switches to exploitation, where the arm with the highest recorded reward is chosen and pulled. Again, the reward is recorded, and the count of that arm's plays is incremented. This continues for the remaining iterations.

## UCB1 Algorithm

The UCB1 algorithm is another Multi-Armed Bandit algorithm, and it accounts for both the number of times an arm has been played and the average reward obtained so far. Here is the Python code implementing the UCB1 algorithm:

```python
import math

def ucb1(arms):
    """UCB1 algorithm for Multi-Armed Bandit problem."""
    rewards = [0] * len(arms)  # rewards for each arm
    plays = [0] * len(arms)  # number of times each arm is played
    total_reward = 0
    
    # Initialization: play each arm once
    for i in range(len(arms)):
        reward = arms[i].pull()
        rewards[i] = reward
        plays[i] = 1
        total_reward += reward
    
    # Main loop
    while True:
        arm_index = -1
        best_ucb = -1
        
        for i in range(len(arms)):
            if plays[i] == 0:
                arm_index = i
                break
            else:
                # Calculate upper confidence bounds for each arm
                ucb = rewards[i] / plays[i] + math.sqrt(2*math.log(sum(plays))/plays[i])

                if ucb > best_ucb:
                    arm_index = i
                    best_ucb = ucb
        
        # Pull chosen arm and update counts and rewards
        reward = arms[arm_index].pull()
        rewards[arm_index] += reward
        plays[arm_index] += 1
        total_reward += reward
        
        # Termination condition: all arms have been played at least once
        if 0 not in plays:
            break
    
    return total_reward
```

In this code, the `arms` list and the `pull()` method of the Bandit object are the same as in the Epsilon Greedy algorithm. The algorithm starts by playing each arm once and recording the reward. After initialization, the algorithm calculates the upper confidence bound for each arm using the current rewards and the number of times each arm has been played. The arm with the highest upper confidence bound is chosen and pulled. The reward is recorded, and the counts of that arm's plays and rewards are incremented. This continues until all arms have been played at least once.

## Thompson Sampling Algorithm

The Thompson Sampling algorithm is another Multi-Armed Bandit algorithm, and it takes into account the probability distribution of the reward function of each arm. Here is the Python code implementing the Thompson Sampling algorithm:


```python
def thompson_sampling(arms):
    """Thompson Sampling algorithm for Multi-Armed Bandit problem."""
    num_arms = len(arms)
    num_iterations = 1000
    total_reward = 0
    
    # Initialize arrays for Bernoulli distribution parameters of each arm
    alpha = [1] * num_arms
    beta = [1] * num_arms
    
    # Main loop
    for t in range(num_iterations):
        # Sample from each arm's Beta distribution and choose arm with highest sample
        samples = [random.betavariate(alpha[i], beta[i]) for i in range(num_arms)]
        arm_index = samples.index(max(samples))
        
        # Pull chosen arm and update Bernoulli distribution parameters and total reward
        reward = arms[arm_index].pull()
        alpha[arm_index] += reward
        beta[arm_index] += 1 - reward
        total_reward += reward
    
    return total_reward
```

In this code, `arms` is again a list of Bandit objects. This algorithm generates a sample from each arm's Beta distribution and chooses the arm with the highest sample. It then pulls that arm and updates the Bernoulli distribution parameters using the observed reward. This continues for a given number of iterations, and the total reward is returned as the output.

These three algorithms – Epsilon Greedy, UCB1, and Thompson Sampling – are all powerful tools in the Multi-Armed Bandit problem, and all played a role in solving the mysterious case presented in this chapter.