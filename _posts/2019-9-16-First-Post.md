---
layout: post
title: This is my first post!
---

### Bayes' Theorem  
Assuming there is a bag of ten-thousand red and blue balls for prize draw. The only information we have is as below:  
- 1% of the balls are inscribed with a special mark and will award the player $2000.  The rest 99% of balls are not inscribed and awarding nothing.  
- 80% of the inscribed balls are painted in red, and 90% of the non-inscribed balls are in blue.  
  
Every player will be presented with the color of a ball drawn by the game host, along with an upfront prize of $1000.  Now, if you are a player and see a red ball, should you walk away with the upfront prize or take the chance and fully reveal the ball?  
  
On the nutshell, 80% of the inscribed balls are red, 90% of the non-inscribed balls are blue, and we are seeing a red ball.  The chance of winning $\$ $2000 seems promising, and we shouldn't be satisfied with only $1000, right?  Well, according to Bayes' Theorem, the probability for a red ball happening to be inscribed might not as high as it appears.
  
Bayes' Theorem is very helpful in building intelligent systems.  For example, a smart defect detector installed on a production line can be used for finding defective items more efficiently. Bayes' Theorem also has presence in many Machine Learning models used for filtering out spam emails or recognizing human speech.  It finds us the true probability from an observation and makes an essential part in decision making.

Since Bayes' Theorem is such a powerful tool for data scientists, let's use it to beat the game in the data scientist way.  
  
We start by looking into the relationship between red/blue balls and inscription.  As 80% of the inscribed balls are red and 90% of non-inscribed balls are blue, we obtain a table below:
  
|                | Red        | Blue        |
| -------------- |:----------:|:-----------:|
| Inscribed      | 80%        | 20%         |
| Non-inscribed  | 10%        | 90%         |
  
We then include the probability of inscribed balls to get the probability distribution of $P(inscribed, red)$, $P(inscribed, blue)$, $P(non-inscribed, red)$ and $P(non-inscribed, blue)$:
  
| Probability distribution |      |       |
|--------------------------|:----:|:-----:|
|                          |  Red | Blue  |
| Inscribed                | 0.8% | 0.2%  |
| Non-inscribed            | 9.9% | 89.1% |
  
A little discussion on the probability table:
- As 1% of the balls are inscribed, and 80% of the inscribed balls are red, we can get that the possibility of balls being both inscribed and red is $80\% \cdot 1\% = 0.8\%$.  Similarly, we can infer that 20% of inscribed balls are blue and get the possibility of balls that are inscribed and blue, which is 0.2%.  
- 99% of the balls are not inscribed, and 90% of them are blue, so possibility of non-inscribed and blue balls becomes $99\% \cdot 90\% = 89.1\%$.  From the same technique, the probability of a ball being non-inscribed and red is 9.9%.  
- the probability distributions add up to 1.  
  
Now, it's time to show the famous Bayes' Theorem:  
  
$\large P(H | O) = \frac{P(O | H)\cdot P(H)}{P(O)}$  
  
Here, $H$ means hypothesis and $O$ means observation.  $P(H | O)$ means the probability of hypothesis $H$ given the observation $O$.  Applying to the price draw above:
- hypothesis ($H$) is that the ball is inscribed
- observation ($O$) is that a red ball has been observed.  

Our goal is to find out how likely $H$ (a ball is inscribed) will be, given $O$ (red color is observed).  Namely, $P(H | O)$.  
  
From basic conditional probability, $P(O | H)\cdot P(H) = \frac{P(O\ and\ H)}{P(H)} \cdot P(H) = P(O\ and\ H)$.  
The equation is then reduced to $P(H | O)=\frac{P(O\ and\ H)}{P(O)}$.  
$P(O\ and\ H)$ is the probability that a ball is red and inscribed, which is 0.8% from the probability distribution table.  $P(O)$ is the probability of a ball being red, which is $0.8\% + 9.9\%=10.7\%$.  
  
And, we get $P(H | O)=\frac{0.8\%}{10.7\%}=7.48\%$.  This means, when a red ball is shown, there is only 7.48% of chance that it is also inscribed.  Based on expected value calculation, seeing a red ball yields only $\$2000 \cdot 7.48\%=\$ 149.6$.  I am not sure about you, but I would prefer taking the $\$ 1000$ upfront prize.  
  
This seems defying the instinct, right?  When $80\%$ of the prize-awarding balls are red, why seeing a red ball only guarantees such a low expected value?  The secret is, there are significantly more red balls that couldn't award you a prize.  
  
We can look at this game more deeply.  Based on the games rules, $1\% \cdot 10,000 = 100$ balls are inscribed, and $80\% \cdot 100 = 80$ inscribed balls are red.  On the other hand, $99\% \cdot 10,000 = 9900$ balls are not inscribed, and $9900 \cdot 10\%=990$ non-inscribed balls are red.  The truth is that, out of $80+990=1070$ red balls, only 80 of them can win you $2000.  
  
Bayes' Theorem is not magic; instead, it points us to look at probability problems with a more complete view.  I am so lucky to learn about it and other data science fundamentals at UBC.  If later I came across any other interesting ideas, they will also be reported here.  Please stay tuned!! 
