# An Intro to the T-Test

T-Tests are key when one wants to determine if there is a meaningful difference between two observed quantitative values when we do not have data about the entire population. Consider the following basic example:

**Example:** Mr. A is a new teacher for Calculus 1 at your local high school. At the end of the school year, the principal wants to determine if Mr. A is a stronger or weaker teacher than the average teacher in the school. The only accessible data is the percentage each student earned in the course for all Calc 1 students. 

*Solution:* Our answer to this question is not as simple as just directly comparing Mr. A's class average to the entire school's average. If Mr. A's average is 72% and the school's average is 73%, there is probably not enough evidence to draw a conclusion. The difference could be due to just noise. To answer this question, we instead use a t-test, which is a type of hypothesis test. We let $\mu_a$ denote Mr. A's class average. We let $\mu_0$ denote the school's average. We form the following set of hypotheses:
$$H_0: \mu_{a} = \mu_{0},$$
$$H_A: \mu_{a} \neq \mu_0.$$
In this formulation, $H_0$ is our null hypothesis and $H_A$ is our alternative hypothesis. The t-test can detect whether the null hypothesis is (likely) false. However, it cannot determine whether the null hypothesis is true. To perform the t-test, we calculate the t-statistic. There are many choices for t-statistics and we will consider the following two: Student's t-statistic and Welsh's t-statistic. Student's t-statistic is the most commonly taught and is the following:
$$t_s = \frac{\mu_a - \mu_0}{\sigma/\sqrt{n}}.$$
In this formulation, $\sigma$ is the standard deviation of the grades of Mr. A's students and $n$ is the number of students. By the Central Limit Theorem, the distribution of sample means is approximately normal. Therefore, we determine the probability of observing these results under a $N(0, 1)$ distribution. If the probability is less than a given threshold, we reject the null and accept the alternative hypothesis.
