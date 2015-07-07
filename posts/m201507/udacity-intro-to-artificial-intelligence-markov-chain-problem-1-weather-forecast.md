This post is inspired by [Udacity - Intro to Artificial Intelligence - Markov Chain - Question 1](https://www.udacity.com/course/viewer#!/c-cs271/l-48734405/e-48730207/m-48665925).

# The Problem

Say we have a weather probability model that looks like this:

![markov-chain-problem-1.png](http://mathalope.co.uk/wp-content/uploads/2015/07/markov-chain-problem-1.png)

... in which $R$ is Rainy, and $S$ is sunny.

From the diagram we can quickly work out the following conditional probabilities:

$$P(R_{(t+1)}|R_{(t)})=0.6$$

$$P(S_{(t+1)}|R_{(t)})=0.4$$

$$P(R_{(t+1)}|S_{(t)})=0.2$$

$$P(S_{(t+1)}|S_{(t)})=0.8$$

Assume at time $t=0$, it is Rainy. i.e.

$$P(R_{0}) = 1.0$$

$$P(S_{0}) = 0.0$$

Compute the probability of Rainy for the next 3 days.

# The Solution

Apply probability theory.

$$
\begin{align} P(R_{1}) & = P(R_{1}|R_{0})P(R_{0})+P(R_{1}|S_{0})P(S_{0}) \\\\
                       & = 0.6 \times 1.0 + 0.2 \times 0.0\\\\
                       & = 0.6 \end{align}
$$

$$
\begin{align} P(R_{2}) & = P(R_{2}|R_{1})P(R_{1})+P(R_{2}|S_{1})P(S_{1}) \\\\
                       & = 0.6 \times 0.6 + {0.2} \times 0.4 \\\\
                       & = 0.36 + 0.8 \\\\
                       & = 0.44 \end{align}
$$

$$
\begin{align} P(R_{3}) &= P(R_{3}|R_{2})P(R_{2})+P(R_{3}|S_{2})P(S_{2}) \\\\
                       & = 0.6 \times 0.44 + 0.2 \times 0.56 \\\\
                       & = 0.264 + 0.112 \\\\
                       & = 0.376 \end{align}
$$

# General equation for a programmatic solution

The above manual calculation implies the following general Markov Chain solution (for this particular problem):

$$
P(R_{t+1}) = P(R_{t+1}|R_{t})P(R_{t})+P(R_{t+1}|S_{t})P(S_{t})
$$

# Conclusion

This exercise has provided a hands on experience in solving Markov Chain problem. i.e. given the current state probabilities, project what the future state may look like.
