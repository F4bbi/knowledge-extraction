# The Reichenbach Reckoning: Sherlock Holmes’ Mathematical Mysteries

These quests are infused with the atmosphere of Victorian mystery, deductive reasoning, and the intrigue of 221B Baker Street. The problems are now framed as cases or puzzles Holmes and Watson might encounter, requiring clever twists and contextual reasoning.

## 1 Written Problems
### 1. The Seating of the Diogenes Club
Sherlock Holmes investigates a clandestine meeting at the Diogenes Club, where 10 distinct members must sit in a row under strict protocols:

a. If no rules bind their arrangement, how many ways can the silent gentlemen be seated?

The number of ways to arrange 10 distinct individuals in a row, considering that each individual can be chosen only once, is simply the factorial of the number of people. That is $10! = 3628800$.

b. Suppose Mycroft Holmes and his aide, bound by mutual distrust, must sit side-by-side to monitor each other—how many arrangements are possible?

There are 9 ways to arrange Mycroft Holmes and his aide so that they are seated side by side. For each of these arrangements, the remaining 8 seats can be filled in $8!$ ways. Additionally, for each of the 9 arrangements, there are 2 possible orderings of Mycroft Holmes and his aide. Therefore, the total number of arrangements is: $9 \times 8! \times 2 = 9! \times 2 = 725760$.

c. If 5 are seasoned inspectors and 5 are novice constables, and no two of the same rank may sit adjacent (lest rivalries flare), how many seating orders hold?

There are two possible starting ranks (inspector or constable), each leading to $5!$ permutations for inspectors and $5!$ for constables. The total number of arrangements is $2×5!×5! = 28800$.

d. If the 10 form 5 pairs of informants and handlers, each pair inseparable due to whispered secrets, how many arrangements emerge?

We can consider the 5 pairs as single entity, so the number of arrangements of them is $5!$. But since each of the pairs can be seated in two ways, the total number of arrangements is $2×2×2×2×2×5! = 3840$.

Deduction: Explain your reasoning as if briefing Watson on the club’s hidden hierarchy.

### 2. The Cipher Arrays of Irene Adler
Irene Adler hides messages in sorted arrays of k distinct integers, each from 1 to n (e.g., 1 ≤ x[0] < x[1] < … < x[k-1] ≤ n). How many such arrays can she devise, as if concealing clues in a locked box?
Deduction: Unravel the pattern as if outwitting her guile.

To recap, the arrays are strictly increasing sequences of $k$ distinct integers from 1 to $n$. The critical insight is that order is enforced by the sorted constraint. Once $k$ distinct numbers are selected, their arrangement is uniquely determined. Thus, the problem reduces to counting combinations of $k$ elements from $n$, as order does not matter beyond selection. This is the basically the binomial coefficient, thus the solution is $\binom{n}{k} = \frac{n!}{(n-k)!k!}$.

### 3. The Paths of the Hound
A mechanical hound roams an $n × m$ grid from $(1,1)$ to $(n,m)$, moving only right or down:
a. With no bounds, how many trails can it leave?

To go from $(1,1)$ to $(n,m)$, the mechanical hound must move down exactly $(n-1)$ times and right exactly $(m-1)$ times. Thus, the hound makes a total of $(n-1) + (m-1) = n + m - 2$ moves. Out of these, we must choose $n-1$ moves to be downward (or equivalently $m-1$). Therefore, the number of paths the hound can make is $\binom{n+m-2}{n-1} = \frac{(n+m-2)!}{(n-1)! \, (m-1)!}$

b. If it must first lurch right (a faulty gear), how many paths remain?

If it must first lurch right, the mechanical hound must move down exactly $n−1$ times and exactly $m−2$ times. Thus, the hound makes a total of $(n−1)+(m−2)=n+m−3$ moves. Out all of these we have to choose $n-1$ moves (or $m-2$), so the mechanical hound can leave $\binom{n+m-3}{n-1} = \frac{(n+m-3)!}{(n-1)!\times(m-2)!}$.

c. If it switches direction exactly thrice (right-to-down or down-to-right), how many routes obey?

Having exactly three switches means that the grid must be at least 3 in size.
Having said that, we have 2 cases in which it can happen to have three switches.

Let us start with the first case, i.e. when the hound starts to go right.

One of the two patterns will necessarily be the following:
- the hound makes $k$ moves to the right, then
- the hound makes $j$ moves downwards, then
- the hound makes $m-k-1$ moves to the right, then
- the hound makes $n-j-1$ moves downwards

Let's calculate how many ways the hound can go right. How many combinations can we make with $k$ and $m-k-1$? Since $k$ can be $1,2,...,m-2$ and $m-k-1$ consequently becomes $m-2,...,2,1$, the hound can make $m-2$ possible combinations by going right.

Similarly, how many combinations can we make with $j$ and $n-j-1$? Since $j$ can be $1,2,...,n-2$ and $n-j-1$ consequently becomes $n-2,...,2,1$, the hound can make $n-2$ possible combinations by going downwards.

Thus, if the hound starts with the right, he can make $(n-2)\ times (m-2)$ possible moves by changing direction exactly three times.

The other pattern will be as follows (if the hound starts downwards):
- the hound makes $j$ moves downwards, then
- the hound performs $k$ moves to the right, then
- the hound makes $n-j-1$ moves downwards
- the hound makes $m-k-1$ moves to the right

Let's calculate how many ways the hound can go down. How many combinations can we make with $j$ and $n-j-1$? Since $j$ can be $1,2,...,n-2$ and $n-j-1$ consequently becomes $n-2,...,2,1$, the hound can make $n-2$ possible combinations by going down.

Similarly, how many combinations can we make with $k$ and $m-k-1$? Since $k$ can be $1,2,...,m-2$ and $m-k-1$ consequently becomes $m-2,...,2,1$, the hound can make $m-2$ possible combinations by going right.

Thus, if the hound starts with down, it can make $(n-2) ´many times (m-2)´ possible moves by changing direction exactly three times.

Putting everything together, if the hound changes direction exactly three times, it can make $(n-2)(m-2) + (n-2)(m-2) = 2 \times (n-2)(m-2)$ possible paths.

### 4. The Poker Game at Reichenbach
Holmes faces Moriarty at a poker table, where all five-card hands from a 52-card deck are equally likely:

a. What is the probability of a flush (all of the same suit), including a royal flush?

A flush requires 5 cards of the same suit. There are 4 suits, each with 13 cards. The number of flushes is $4×\binom{13}{5}=4×1287=5148$. The total number of possible hands is $2598960$. Thus, the probability is $\frac{5148}{2598960} = 0.00197$.

b. What is the probability of two pairs (a, a, b, b, c, distinct values)?

The total number of possible hands is $\binom{52}{5}=2598960$ as we said before.
To form a two-pair hand, we have $13 \cdot \binom{4}{2} = 78$ possible combinations, because 4 are the suits and there are 13 ranks for each suit. After choosing the first value, we have 12 remaining values to choose from for the second pair (because the value of the first one has already been chosen, and if we chose it again it would be a four of a kind) multiplied by $\binom{4}{2}$, which makes 36. Finally, there remain $11 \cdot 4=44$ ways to choose the last card. Thus, the probability of two pairs is $\frac{78 \cdot 36 \cdot 44}{2598960} = 0.0475$.

c. What is the probability of four pairs (a, a, a, b, distinct)?
Deduction: Calculate the probabilities as if you were calling Moriarty's bluff.

The total number of possible hands is $\binom{52}{5}=2,598,960$ as we said before.
To get four of a colour we have 13 different combinations and then we are left with 48 cards to choose from. The probability of getting a four of a colour is therefore equal to $\frac{13 \cdot 48}{2598960} = 0.00024$.

### 5. The Binary Telegram of Baskerville
A telegraph sends M 0’s and N 1’s in random order. What’s the chance the first r bits hold exactly k 1’s, as if decoding a hound’s howl?
Deduction: Reason through the static as if time is running out.

Let us proceed in order. The total number of ways to arrange M zeros and N ones is $\binom{M+N}{N}$, but since we are only interested in the first $r$ bits, the total is $\binom{M+N}{r}$. We now proceed to calculate how many combinations of 0 and 1 there are in which there are exactly $k$ ones (and consequently $r-k$ zeros). They will be exactly $\binom{N}{k} \cdot \binom{M}{r-k}$. Thus, the chance the first $r$ bits hold exactly $k$ 1's is $\frac{\binom{N}{k} \cdot \binom{M}{r-k}}{\binom{M+N}{r}}$.

### 6. The Menagerie of Moriarty
Holmes uncovers Professor Moriarty’s scheme to display 3 bird species and 3 reptile species, selected from 8 birds and 6 reptiles, in a sinister zoo:
a. If Moriarty chooses freely, how many exhibits can he craft?

Moriarty can freely select 3 birds from 8 and 3 reptiles from 6. The number of exhibits is $\binom{8}{3} \cdot \binom{6}{3}= 56 \cdot 20 = 1120$

b. Two birds—one a hawk with a piercing cry, the other a raven with a deadly glare—cannot coexist without chaos. How many exhibits avoid this peril?

We only have to remove the combinations in which the hawk and the raven appear, which are exactly 6 (2 positions are already fixed for the hawk and the raven, and for the third one 6 birds remain).
The number of exhibits is $(\binom{8}{3} - 6) \cdot \binom{6}{3}= 1000$

c. A venomous parrot and a cobra, when paired, unleash a toxic fog. How many exhibits dodge this trap?

Like point b, just remove all combinations in which the parrot and cobra appear from the total. The combinations in which the parrot does not appear are $\binom{7}{2}$ because one position is fixed by the parrot and we are left with 2 in which we can choose 7 birds. Similarly, the combinations in which the cobra does not appear are $\binom{5}{2}$ because one position is fixed by the cobra and we are left with 2 in which we can choose 5 reptiles. The number of exhibits is $1120 - (\binom{7}{2} \cdot \binom{5}{2}= 910$.

### 7. The Investments of Baker Street
Holmes secures £20 million to fund 4 shadowy enterprises, investing in £1 million units, each with a minimum stake: £1M, £2M, £3M, £4M.
a. If all 4 must be funded to foil Moriarty’s network, how many strategies exist?

(Having no idea how to approach such a problem, I googled and discovered the existence of the combinatorial counting technique **stars and bars**, which is fundamental to solving problems of this type).
Since each enterprise has a minimum investment requirement, we first need to subtract the minimum required amounts from 20, that is $1+2+3+4=10$. We then have 10M to be freely distributed among all 4 enterprises without restrictions. As I stated above, we have to use the combinatorial counting technique stars and bars. We first imagine the 10M as balls: ⚪⚪⚪⚪⚪⚪⚪⚪⚪⚪. To separate the money among the 4 enterprises, we insert 3 barriers between the balls to divide the groups. For example ⚪⚪|⚪⚪⚪|⚪⚪⚪⚪|⚪
means that we give 2M to the first enterprise, 3M to the first enterprise, 4M to the third enterprise and 1M to the fourth enterprise. In this way the millions available will always be 10 but using the barriers we can calculate all possible ways to distribute them. It is therefore a matter of calculating all possible positions where I can put barriers on 13 available positions (10 (balls) + 3 (barriers)). Therefore, there are exactly $\binom {13}{3}=286$ strategies.

b. If at least 3 must be backed (to keep the web intact), how many plans work?

In order to calculate all the ways there are to distribute the 20 million among the 4 enterprises by ensuring that at least 3 enterprises receive the financing, it is sufficient to add up the cases in which all 4 enterprises are financed and the cases in which exactly 3 enterprises are financed. We have already calculated the first one in the previous exercise, i.e. $286$. For the second, we must exclude each enterprise in turn and calculate how many ways there are to finance the other 3.

We start by excluding the first one. If enterprise 1 is removed, we have 11 million that we can distribute among the other three. We then use the same tactic as above, taking into account that this time we have 2 barriers. If firm 1 is removed, we have $\binom {11+2}{2}=78$ ways to allocate the other 3 firms.

If firm 2 is removed, we have 12M which we can distribute among the other 3 firms. We then have $\binom {12+2}{2}=91$ ways to arrange the other 3 firms.

If firm 3 is removed, we have 13M which we can distribute among the other 3 firms. We then have $\binom {13+2}{2}=105$ ways to arrange the other 3 firms.

If firm 4 is removed, we have 14M which we can distribute among the other 3 firms. We then have $\binom {14+2}{2}=120$ ways to dispose the other 3 firms.

Finally, if at least 3 must be supported, there are $286+78+91+105+120=680$ ways to do so.

### 8. The Coding Conundrum of Scotland Yard
Holmes probes a cryptography school where 100 agents study 3 courses—Java, C++, Python—under Lestrade’s watch:
Java: 27 agents; C++: 28; Python: 20.
12 crack Java and C++; 5 master Java and Python; 8 excel in C++ and Python.
2 prodigies conquer all three.

a. What’s the chance a random agent has evaded all courses, lurking in the shadows?

To compute the chance a random agent has evaded all courses, it's sufficient to calculate $\frac{\text{\# of students that have evaded all courses}}{\text{\# of students}}$. We have the total number of students, but we have to find the number of students that do no courses. We can calculate this subtracting from the total of students the students who do at least one course, that is $100 - J \cup C \cup P$, where J stands for Java, C for C++ and P for Python.
$$
\begin{aligned}
100 - J∪C∪P &= 100 - (J + C + P − J∩C − C∩P − J∩P + J∩C∩P)\\ \\ &= 100 - (27 + 28 + 20 - 12 - 5 - 8 + 2)\\ \\ &= 48
\end{aligned}
$$

The chance a random agent has evaded all courses $\frac{48}{100} = 0.48$

b. What’s the chance an agent studies exactly one, avoiding the others’ scrutiny?

To compute the chance an agent studies exactly one course, it's sufficient to calculate $P(Only J) + P(Only C) + P(Only P)$. Let's compute each of them:
$$Only J = J - J∩C− J∩P + J∩C∩P = 27 - 12 - 5 + 2 = 12$$
$$Only C = C - J∩C− C∩P + J∩C∩P = 28 - 12 - 8 + 2 = 10$$
$$Only P = P − J∩P - C∩P + J∩C∩P = 20 - 5 - 8 + 2 = 9$$

The chance an agent studies exactly one course is $\frac{12+10+9}{100}=0.31$

c. If two agents are nabbed, what’s the odds at least one knows a course? Give a final number.

To calculate the odd at least one of two agents know a course it's sufficient to compute the probability that both of them evade all courses and then making $1 - P(\text{both evade})$. From the question a we know the probability that a single agent evades all courses, that is $0.48$. The probability that two randomly chosen agents evade all courses is $\frac{48}{100} \cdot \frac{47}{99} = 0.228$. We can now calculate the odds at least one of the two randomly chosen agents know a course, that is $1-0.228=0.772$.

### 9. The Passwords of the Naval Treaty
A spy tackles n distinct passwords, one unlocking a treaty:
a. Trying randomly and discarding failures, what’s the chance the k-th attempt succeeds?

If the k-th attempt succeeds, it means the $k-1$ attemps must fail. The probability of failing is $\frac{n-1}{n}$, the probability of succeeding is $\frac{1}{n}$, but since we discard failures the events are dipendent and we have to decrease the total of password at each fail. Let's compute the final probability:

$$
\begin{aligned}
P(\text{k-th succeeds}) = \overbrace{\frac{n-1}{n} \times \frac{n-2}{n-1} \times \cdots \times \frac{n-k+1}{n-k+2}}^{k-1 \text{ fails}} \times \overbrace{\frac{1}{n-k+1}}^{\text{k-th success}}
\end{aligned}
$$

In addition, we can see that every numerator simplifies with the. next denominator, hence the final result simplifies to $\frac{1}{n}$.

b. Trying randomly without discarding, stopping at success, what’s the chance the k-th try wins?

The reasoning is similar of the precedent point, but this time every event is indipendent, thus we do not have to decrease the total of password at each fail.
The chance the k-th try wins is:

$$
\underbrace{\left(\frac{n-1}{n}\right)^{k-1}}_{\text{k-1 fails}} \times \underbrace{\frac{1}{n}}_{\text{k-th success}}
$$

### 10. The Dice of the Speckled Band
Holmes rolls a six-sided die six times to crack a gypsy code:
a. What’s the chance two numbers appear thrice each (e.g., three 4s, three 6s)?

First, we have to compute how many ways there are that two numbers (that will appear three times each) appear twice. There are $\binom{6}{2} = 15$ ways to select two numbers from the six available. For each of these combinations, we have $\binom{6}{3} = 20$ ways in which we can arrange the two numbers. Finally, in total we have $6^6$ possible combinations. Then, the chance two numbers appear thrice each is $\frac{15 \times 20}{6^6} = 0.0064$.

b. What’s the chance exactly one number hits thrice, no more, no less?

First, there are 6 possible numbers on the die. Let's take for example the case where the number 1 has to hit exactly thrice. The numbers of ways it can appear exactly 3 times in 6 throws is $\binom{6}{3} = 20$. For each of this disposizione, there can be 5 other numbers that can appear 3 times (that are $5^3$), but we must exclude the combinations where there are the same 3 numbers (that are $5$, 222, 333, 444, 555, 666). Putting it all together, the chance exactly one number hits thrice is $\frac{6 \times 20 \times (5^3 - 5)}{6^6} = 0.309$.

### 11. The Letters of the Red-Headed League
Holmes dispatches 20 distinct letters to 12 unique informants, each landing randomly. What’s the chance 4 get exactly 2 letters and 3 get exactly 4, the rest empty-handed?

Each of the 20 distinct letters can go to any of the 12 informants, then the total combinations are $12^{20}$.

First, let's compute the number of ways we can partition the 12 informants into 3 groups of 4,3 and 5 informants, that is is $\binom{12}{4, 3, 5} = \frac{12!}{4! \cdot 3! \cdot 5!} = 27720$. We have chosen the "recipients", now we have to assign the 20 distinct letters. We have to keep in consideration that 4 informants get 2 letters each (so the groups will be like 2, 2, 2, 2), and 3 informants get 4 letters each (so the groups will be like 4, 4, 4). The number of ways to partition the 20 letters into these groups are $\frac{20!}{(2!)^4 \cdot (4!)^3}$. Putting it all together, the chance 4 get exactly 2 letters and 3 get exactly 4, the rest empty-handed, is:

$$
\frac{\left( \frac{12!}{4! \cdot 3! \cdot 5!} \right) \cdot \left( \frac{20!}{(2!)^4 \cdot (4!)^3} \right)}{12^{20}} = 3.3 \times 10^{-6}
$$

### 12. The Buckets of Bohemia
m clues are hashed into N buckets by a rogue algorithm, all N^m outcomes equal. What’s the chance exactly k land in the first bucket?

Each of the m clues can independently go into any of the N buckets, then the chance exactly k land in the first bucket is simply the Probability Mass Function of the binomial:

$$P(X = k) = \binom{m}{k} \left(\frac{1}{N}\right)^k \left(1 - \frac{1}{N}\right)^{m - k}$$

### 13. Coding (Sherlock Holmes Edition)
1. The Game of the Final Problem
Holmes and Moriarty duel with a device spitting integers from 1 to 100. Holmes adds to S (from 0) until S > 100, noting his last number x. Moriarty resumes, adding until S > 200, noting y. The higher wins. Simulate 100,000 rounds in Python 3 and estimate Moriarty’s victory odds, as if outsmarting Holmes at Reichenbach.
Deduction: Code as if the fate of London hangs in the balance—comment your logic.

Assuming that x and y are the numbers that make the Holmes and Moriarty counters exceed 100 and 200, here's the code.

```python
import random

moriarty_wins = 0
simulations = 100000

for _ in range(simulations):
    # Holmes' turn
    s = h = m = 0

	# keep summing the generated number to s until it exceeds 100
    while h <= 100:
        num = random.randint(1, 100)
        s += num
        if s > 100:
            h = num
            break
    
    # Moriarty's turn
    # keep summing the generated number to s until it exceeds 200
    while m <= 200:
        num = random.randint(1, 100)
        s += num
        if s > 200:
            m = num
            break
    
    if m > h:
        moriarty_wins += 1

victory_prob = moriarty_wins / simulations
print("Moriarty's victory probability: " + str(victory_prob))
```