# An Intro to the T-Test

T-Tests are key when one wants to determine if there is a meaningful difference between two observed quantitative values when we do not have data about the entire population. Consider the following basic example:

**Example:** Mr. A is a new teacher for Calculus 1 at your local high school. At the end of the school year, the principal wants to determine if Mr. A is a stronger or weaker teacher than the average teacher in the school. The only accessible data is the percentage each student earned in the course for all Calc 1 students. 

*Solution:* Our answer to this question is not as simple as just directly comparing Mr. A's class average to the entire school's average. If Mr. A's average is 72% and the school's average is 73%, there is probably not enough evidence to draw a conclusion. The difference could be due to just noise. To answer this question, we instead use a t-test, which is a type of hypothesis test. We let $\mu_a$ denote Mr. A's class average. We let $\mu_0$ denote the school's average. We form the following set of hypotheses:
$$H_0: \mu_{a} = \mu_{0},$$
$$H_A: \mu_{a} \neq \mu_0.$$
In this formulation, $H_0$ is our null hypothesis and $H_A$ is our alternative hypothesis. The t-test can detect whether the null hypothesis is (likely) false. However, it cannot determine whether the null hypothesis is true. To perform the t-test, we calculate the t-statistic. There are many choices for t-statistics and we will consider the following two: Student's t-statistic and Welch's t-statistic. Student's t-statistic is the most commonly taught and is the following:
$$t_s = \frac{\mu_a - \mu_0}{\sigma/\sqrt{n}}.$$
In this formulation, $\sigma$ is the standard deviation of the grades of Mr. A's students and $n$ is the number of students. By the Central Limit Theorem, the distribution of sample means is approximately normal. Therefore, we determine the probability of observing these results under a $t$-distribution, which limits to $N(0, 1)$ as the degrees of freedom tend towards infinity. If the probability is less than a given threshold, we reject the null and accept the alternative hypothesis.

### A Note on Power

When discussing a statistical hypothesis test, power refers to the ability to reject the null when the null is false. Formally, we have $$P = \text{Pr} (\text{Accept } H_A : H_0 \text{ is False.})$$ For a t-test, as sample size increases, so does power and this heuristically makes sense. Consider the extreme scenario for the example above: the school's average is 70% and Mr. A's class average is 100%. If Mr. A's class only has two students, maybe he got lucky and had two very strong students. If instead, Mr. A had 200 students then it is unlikely that this performance is simply the result of noise.

Mathematically, when we rewrite the t-statistic as $$\sqrt{n}\frac{\mu_a - \mu_0}{\sigma}$$ it is apparent that the magnitude of the statistic increases as $n$ increases, thus, making the null hypothesis easier to reject.

## Unpaired Two-Sample T-Tests

We use one-sample t-tests when working with observational data with a null hypothesis. However, for an experiment we often have two groups that we compare. An A/B test is a statistical experiment where we change one feature and measure the change in behavior. Let's consider the New York Times. NYT's ads department would like to include video ads on each article because video ads bring in more revenue than static banner ads, however, the decision maker is concerned that readers will spend less time on any given article because they are annoyed by the ad. The ads department asks for us, as a data scientist, to determine if this is true or not. We set up the following experiment: we select an article, then, for a 24 hour window, every time a reader visits the article we randomly assign a static banner ad or video ad, and finally, we record how long the reader remained on the page. To perform our analysis, we want to compare the average time readers in one group spent on the article compared to the other group. 

Here, our analysis is a little bit more complicated than when we applied Student's One-Sample t-test. Now, we have two groups with similar, but not equal, sample sizes and differing standard deviations. Student's t-test can be adapted for equal sample sizes and equal standard deviations: essentially, if the means of each group are $\mu_A$ and $\mu_B$ then we test with the null hypothesis $H_0: \mu_A - \mu_B = \mu_{A-B} = 0$. When the sample sizes and standard deviations are not equal, we use Welch's t-test. The t-statistic is
$$t = \frac{\mu_A - \mu_B}{\sqrt{\frac{\sigma_A^2}{N_A} + \frac{\sigma_B^2}{N_B}}}$$









