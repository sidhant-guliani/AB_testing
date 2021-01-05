# AB_testing

Let’s imagine you work on the product team at a medium-sized online e-commerce business. 
The UX designer worked really hard on a new version of the product page, with the hope that it will lead to a higher conversion rate. 
The product manager (PM) told you that the current conversion rate is about 13% on average throughout the year, and that the team would be happy with an increase of 2%, 
meaning that the new design will be considered a success if it raises the conversion rate to 15%.


Before rolling out the change, the team would be more comfortable testing it on a small number of users to see how it performs, 
so you suggest running an A/B test on a subset of your user base users.


Step1: Formulating a hypothesis

First things first, we want to make sure we formulate a hypothesis at the start of our project. 
This will make sure our interpretation of the results is correct as well as rigorous.

Given we don’t know if the new design will perform better or worse (or the same?) as our current design, we’ll choose a two-tailed test:

              Hₒ: p = pₒ

              Hₐ: p ≠ pₒ
              
where p and pₒ stand for the conversion rate of the new and old design, respectively. We’ll also set a confidence level of 95%:

              α = 0.05

The α value is a threshold we set, by which we say “if the probability of observing a result as extreme or more (p-value) is lower than α, then we reject the Null hypothesis”. Since our α=0.05 (indicating 5% probability), our confidence (1 — α) is 95%.

Don’t worry if you are not familiar with the above, all this really means is that whatever conversion rate we observe for our new design in our test, we want to be 95% confident it is statistically different from the conversion rate of our old design, before we decide to reject the Null hypothesis Hₒ.


Step 2 Choosing a sample size

It is important to note that since we won’t test the whole user base (our population), the conversion rates that we’ll get will inevitably be only estimates of the true rates.

The number of people (or user sessions) we decide to capture in each group will have an effect on the precision of our estimated conversion rates: the larger the sample size, the more precise our estimates (i.e. the smaller our confidence intervals), the higher the chance to detect a difference in the two groups, if present.

On the other hand, the larger our sample gets, the more expensive (and impractical) our study becomes.

                                      So how many people should we have in each group?
                                      
The sample size we need is estimated through something called Power analysis, and it depends on a few factors:

          Power of the test (1 — β) — This represents the probability of finding a statistical difference between the groups in our test when a difference is actually present. This is usually set at 0.8 by convention (here’s more info on statistical power, if you are curious)

          Alpha value (α) — The critical value we set earlier to 0.05

          Effect size — How big of a difference we expect there to be between the conversion rates
          
Step 3: Sampling of data

step 4. Testing the hypothesis

The last step of our analysis is testing our hypothesis. Since we have a very large sample, we can use the normal approximation for calculating our p-value (i.e. z-test).

Again, Python makes all the calculations very easy. We can use the statsmodels.stats.proportion module to get the p-value and confidence intervals:

Step 5: Analysing the results

If  our p-value is way above our α=0.05 threshold, we cannot reject the Null hypothesis Hₒ, which means that our new design did not perform significantly different (let alone better) than our old one :(

