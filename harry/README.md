# Hogwarts Quests - Assignment 2

## 1.

You are tracking the distance to the Hogwarts Express. A magical instrument reports it’s 100 leagues away. Before the reading, your belief about the distance $D$ was a Gaussian $D ∼ N(µ = 98, σ^2 = 16)$. The instrument’s reading is the true distance plus Gaussian noise $(N(0, 4))$.

a. What is the PDF of your prior belief of the train’s true distance?

The Probability Density Function of the prior belief about the train's true distance is given by the Gaussian distribution with $µ = 98$ and $σ^2 = 16$, that is $f(x) = \frac{1}{4\sqrt{2\pi}} e^{-\frac{(x - 98)^2}{32}}$.

b. What is the probability density of seeing a reading of 100 leagues, given the true distance is t?

Let's call R the random variable that represents seeing a reading of $r$ pages, in this case 100. In shorts, we have to compute $P(R = 100\ |\ D = t)$, where $R$, as stated in the text, is the true distance plus a Gaussian noise $(N(0, 4))$. This means that the distribution of $R$ is $t + N(0, 4) = N(t, 4)$. Then:

$$P(R = 100\ |\ t) = \frac{1}{2\sqrt{2\pi}} e^{-\frac{(100 - t)^2}{8}}$$

c. What is the PDF of your posterior belief (after the reading) of the train’s true distance? (You can leave a constant and don’t need to simplify).

In shorts, we have to compute $P(D = t\ |\ R=100)$. We can calculate this using Bayes' Theorem, that is:

$P(D=t\ |\ R=100) = \frac{P(R=100\ |\ D=t) \times P(D=t)} {P(R=100)}$

Since the question allows us to leave a constant:

$P(D=t\ |\ R=100) = C \times P(R=100\ |\ D=t) \times P(D=t)$

We have already found $P(D=t)$ in part (a) and $P(R=100\ |\ D=t)$ in part (b), so we have only to substitute:

$$P(D=t | R=100) = C \times \frac{1}{2\sqrt{2\pi}} e^{-\frac{(100 - t)^2}{8}} \times \frac{1}{4\sqrt{2\pi}} e^{-\frac{(t - 98)^2}{32}}$$

We can combine the constant terms into a single proportionality constant:

$$P(D=t | R=100) = C \times e^{-\frac{(100 - t)^2}{8}} \times e^{-\frac{(t - 98)^2}{32}} = C \times e^{-\frac{(100 - t)^2}{8} -\frac{(t - 98)^2}{32}}$$

## 2.

On average, 5.5 owls arrive at the Owlery per minute. What is the probability that:

a. More than 7 owls will arrive in the next minute?

First, we decide to model the owl arrivals using a Poisson distribution, since we're looking at the number of events (owl arrivals) occurring in a fixed interval of time, given a known average rate of occurrence, and assuming the events happen independently.
The Probability Mass Function (PMF) for a Poisson distribution is:

$$P(X=k) = \frac{λ^k e^{-λ}}{k!}$$

In this case, we want to compute $P(X > 7) = 1 - P(X \leq 7)$, where $λ=5.5$.
Let's do that:

$$P(X > 7) = 1 - P(X \leq 7) = 1 - \sum_{k=0}^7 \frac{e^{-5.5} (5.5)^k}{k!} = 0.19051$$

b. More than 13 owls will arrive in the next 2 minutes?

The idea is the same as before, but note that the rate is $λ=5.5$ owls per minute; therefore, for this case, $λ=5.5 \times 2 = 11$. As before:

$$P(X > 13) = 1 - P(X \leq 13) = 1 - \sum_{k=0}^{13} \frac{e^{-11} (11)^k}{k!} = 0.21870$$

c. More than 15 owls will arrive in the next 3 minutes?

The idea is the same as before, but note that the rate is $λ=5.5$ owls per minute; therefore, for this case, $λ=5.5 \times 3 = 16.5$. As before:

$$P(X > 15) = 1 - P(X \leq 15) = 1 - \sum_{k=0}^{15} \frac{e^{-16.5} (16.5)^k}{k!} = 0.58198$$

## 3.

The median of a continuous random variable (like the height of a gnome) having cumulative distribution function $F$ is the value $m$ such that $F(m) = 0.5$. Find the median of $X$ (in terms of distribution parameters) if:

a. $X ∼ Uni(a, b)$ (Uniform distribution, like the spread of Floo powder).

For a [uniform distribution](https://chrispiech.github.io/probabilityForComputerScientists/en/part2/uniform/), the CDF is given by:

$$F(x) = \frac{x - a}{b - a} \quad \text{for } a \le x \le b$$

Setting $F(m)=0.5$:

$$\frac{m - a}{b - a} = 0.5 \quad \Longrightarrow \quad m - a = 0.5(b - a)$$
so
$$m = a + 0.5(b - a) = \frac{a + b}{2}$$

b. $X ∼ N(µ, σ^2)$ (Normal distribution, like scores on the O.W.L.s).

A normal distribution is symmetric about its mean, thus the median is equal to the mean:
$$m = \mu$$

## 4.

Let $X_i$ be the number of students visiting the Hogwarts library in week $i$, where $X_i ∼ N(2200, 52900)$. Assume weekly visits $X_i$ are independent.

a. What is the probability that the total number of visitors in the next two weeks exceeds 5000?

First, we can define the total number of visitors over two weeks as $S = X_1 + X_2$, and [since the sum of independent normal variables is a normal](https://chrispiech.github.io/probabilityForComputerScientists/en/part4/summation_vars/#normals), $S ∼ N(2200 + 2200, 52900+52900) = N(4400, 105800)$.

We only need to calculate $P(S>5000)$, using Python or using the integral, that is $0.0325$.

b. What is the probability that the weekly number of visitors exceeds 2000 in at least 2 of the next 3 weeks?

Let's first compute the probability that the number of visitors exceeds 2000 for any given week:

$P(X_i > 2000) = 1 - \int_{0}^{2000} \frac{1}{\sqrt{2\pi \cdot 52900}} \exp\left( -\frac{(x - 2200)^2}{2 \cdot 52900} \right)\ dx = 0.8077$.

Now, let's call $Y$ be the number of weeks (out of 3) with more than $2000$ visitors.
Surely, $Y$ follows a binomial distribution with $3$ trials and $p=0.8078$.

Let's compute it:

$$
\begin{aligned}
P(Y \ge 2) &= P(Y=2) + P(Y=3) \\ \\
&= \binom{3}{2}(0.8078)^2(1-0.8078) + \binom{3}{3}(0.8078)^3 \\ \\
&= 3 \cdot (0.8078)^2 \cdot 0.1922 + (0.8078)^3 \\ \\
&= 0.9033
\end{aligned}
$$

## 5.

Let X, Y , and Z be independent random variables representing the magical power levels of three Hogwarts students, where $X ∼ N(µ_1, σ_1^2)$ (Gryffindor), $Y ∼ N(µ_2, σ_{2}^{2})$ (Hufflepuff), and $Z ∼ N(µ_3, σ_3^2)$ (Ravenclaw).

a. Let $A = X + Y$. What is the distribution of the combined power A?

For any two independent normal random variables $X ∼ N(µ_1, σ_1^2)$ and $Y ∼ N(µ_2, σ_{2}^{2})$ the sum of those two random variables is another normal: $A = X+Y ∼ N(μ_1+μ_2,σ_1^2+σ_2^2)$.

b. Let $B = 5X + 2$. What is the distribution of B (perhaps after a powerenhancing charm)?

If $X$ is a Normal such that $X∼N(μ,σ_1)$ and $B$ is a linear transform of $X$ such that $B=aX+b$ then $B$ is also a Normal where: $B∼N(aμ+b,a^2σ^2)$, then $B∼N(5μ+2,25σ^2)$.

c. Let $C = aX − bY + c^2Z$, where $a$, $b$, and $c$ are real-valued constants representing spell modifiers. What is the distribution (and parameters) for C? Show how you derived your answer.

As before, $C$ is a normal. Let's start by calculating its mean, that is simply $\mathbb{E}[C] = aμ_1​−bμ_2​+c^2μ_3​$

Let's now calculate the variance. Remember that the variance is not linear like expectation: $\text{Var}(aX) = a^2 \text{Var}(X)$.
Then $\text{Var}(C) = a^2\sigma_1^2 + b^2\sigma_2^2 + (c^2)^2\sigma_3^2 = a^2\sigma_1^2 + b^2\sigma_2^2 + c^4\sigma_3^2$

Putting all together: $C \sim \mathcal{N}\left(a\mu_1 - b\mu_2 + c^2\mu_3, a^2\sigma_1^2 + b^2\sigma_2^2 + c^4\sigma_3^2\right)$

## 6.

The joint probability density function of continuous random variables X (skill in Potions) and Y (skill in Charms) is given by $f_{X,Y}(x, y) = c\frac{y}{x}$ where $0 < y < x < 1$.

a. What is the value of $c$ for this to be a valid probability density function?

To be a valid PDF, the total integral over the region must equal 1:

$$\int_{x=0}^{1} \int_{y=0}^{x} c \cdot \frac{y}{x} \, dy \, dx = 1$$

Let's compute the inner integral first:

$$\int_{y=0}^{x} \frac{y}{x} \, dy = \frac{1}{x} \int_{0}^{x} y \, dy = \frac{1}{x} \cdot \left[ \frac{y^2}{2} \right]_0^x = \frac{1}{x} \cdot \frac{x^2}{2} = \frac{x}{2}$$

Now substitute into the outer integral:

$$\int_{x=0}^{1} c \cdot \frac{x}{2} \, dx = c \cdot \int_{0}^{1} \frac{x}{2} \, dx = c \cdot \left[ \frac{x^2}{4} \right]_0^1 = c \cdot \frac{1}{4}$$

Set this equal to 1:

$$c \cdot \frac{1}{4} = 1 \quad \Rightarrow \quad c = 4$$

b. Are Potion skill ($X$) and Charm skill ($Y$) independent? Explain.

Two variables $X$ and $Y$ are independent if

$$f_{X,Y}(x, y) = f_X(x) \cdot f_Y(y)$$

Let's compute first the marginal density function of $X$:

$$f_X(x) = \int_{y=0}^{x} f_{X,Y}(x, y) \, dy = \int_{0}^{x} 4 \cdot \frac{y}{x} \, dy = \frac{4}{x} \cdot \int_0^x y \, dy = \frac{4}{x} \cdot \frac{x^2}{2} = 2x$$

Now the marginal density function of $Y$:

$$
\begin{aligned}
f_Y(y) &= \int_{x=y}^{1} f_{X,Y}(x, y) \, dx = \int_{y}^{1} 4 \cdot \frac{y}{x} \, dx = 4y \cdot \int_{y}^{1} \frac{1}{x} \, dx \\ \\
&= 4y \cdot \left[ \ln x \right]_y^1 = 4y \cdot (\ln 1 - \ln y) = -4y \ln y
\end{aligned}
$$

In the previous answer we discovered that $f_{X,Y}(x, y) = 4\frac{y}{x}$, thus we can conclude that:

$$4\frac{y}{x} \neq -8 \cdot x \cdot y \cdot ln(y)$$

The answer is no, $X$ and $Y$ are not independent.

c. What is the marginal density function of $X$?

We have computed it in the previous answer:

$$f_X(x) = \int_{y=0}^{x} f_{X,Y}(x, y) \, dy = \int_{0}^{x} 4 \cdot \frac{y}{x} \, dy = \frac{4}{x} \cdot \int_0^x y \, dy = \frac{4}{x} \cdot \frac{x^2}{2} = 2x$$

d. What is the marginal density function of $Y$?

We have computed it in the first answer:

$$
\begin{aligned}
f_Y(y) &= \int_{x=y}^{1} f_{X,Y}(x, y) \, dx = \int_{y}^{1} 4 \cdot \frac{y}{x} \, dx = 4y \cdot \int_{y}^{1} \frac{1}{x} \, dx \\ \\
&= 4y \cdot \left[ \ln x \right]_y^1 = 4y \cdot (\ln 1 - \ln y) = -4y \ln y
\end{aligned}
$$

## 7.

Choose a number $X$ at random from the set of house points $\{1, 2, 3, 4, 5, 6\}$ awarded by Professor McGonagall. Now choose a number $Y$ at random from the subset of points no larger than $X$, $\{1, . . . , X\}$.

a. Determine the joint probability mass function of $X$ (initial points) and $Y$ (second random selection).

Let's discuss about the random variable $X$.
$X$ is uniformly distributed over $\{1, 2, 3, 4, 5, 6\}$, thus:

$$P(X = x) = \frac{1}{6} \quad \text{for } x \in \{1, 2, \dots, 6\}$$

Now the random variable $Y$.
Given $X = x$, $Y$ is uniformly distributed over $\{1, 2, \dots, x\}$, thus:

$$P(Y = y \mid X = x) = \frac{1}{x} \quad \text{for } y \leq x$$

Putting all together:

$$
P(X = x, Y = y) =
\begin{cases}
\frac{1}{6} \cdot \frac{1}{x} & \text{if } 1 \leq y \leq x \leq 6, \\ \\
0 & \text{otherwise}
\end{cases}
$$

b. Determine the conditional mass function $P(X = j|Y = i)$ as a function of $i$ and $j$.

Using Bayes’ rule:

$$P(X = j \mid Y = i) = \frac{P(Y = i \mid X = j) \cdot P(X = j)}{P(Y = i)}$$

From the answer before, we know that $P(Y = i \mid X = j) = \frac{1}{j}$, while $P(X = j) = \frac{1}{6}$.

We need to compute the denominator $P(Y = i)$, that is:

$$P(Y = i) = \sum_{j = i}^{6} P(X = j, Y = i) = \sum_{j = i}^{6} \frac{1}{6j}$$

So putting it all together:

$$P(X = j \mid Y = i) = \frac{\frac{1}{6j}}{\sum_{k=i}^{6} \frac{1}{6k}} = \frac{\frac{1}{j}}{\sum_{k=i}^{6} \frac{1}{k}} \quad \text{for } i \leq j$$

c. Are $X$ and $Y$ independent? Explain.

No, the value of $Y$ is constrained by $X$ ($Y \leq X$), so knowledge of $Y$ affects the possible values of $X$. More formally, if $X$ and $Y$ are independent:

$$P(X = j, Y = i) = P(X = j) \cdot P(Y = i) \quad \text{for all } i, j$$

From part (a) we have:

- $P(X = j, Y = i) = \frac{1}{6j}$
- $P(X = j) = \frac{1}{6}$
- $P(Y = i) = \sum_{j=i}^{6} \frac{1}{6j}$

Finally:

$$P(X = j) \cdot P(Y = i) = \frac{1}{6} \cdot \sum_{k=i}^{6} \frac{1}{6k} \ne \frac{1}{6j}$$

We can confirm that $X$ and $Y$ are not independent.
