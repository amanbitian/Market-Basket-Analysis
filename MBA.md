Market Basket Analysis: Calculating the Forgotten 'Significance-of-the-Significance'


Market basket analysis, otherwise known as association rules, is probably well-known to any Data Scientist or Analyst. On the surface, it looks pretty simple, like something you can just get your software to spit out for you without much further thought to it.

However, it is deceptively simple as two considerations are often overlooked. First, let's have a recap of what the different terms output in your association rules summary mean:

Support: P(A intersect B)
Lay meaning: frequency of co-occurrence

Confidence: P(A intersect B)/P(A)
Lay meaning: likeliness of co-occurring given A's presence

Lift: P(A intersect B)/(P(A)*P(B))
- Likelihood of co-occurring compared to the random occurrence of A and B together, i.e. if A and B aren't related and just occurred independently of each other

As usual, lift here refers to how well a model is doing in relation to a 'naive rate' or what folks in my team used to call a 'random rate,' the latter of which I find more intuitive as it reminds you to think of ways of calculating how the results would appear if everything just occurred by chance, i.e. typically, with independence assumptions. In normal classification models, people sometimes calculate the lift on their model using their confusion matrix over and beyond calculating the usual F1s, precision, recall, specificity, etc.

However, apparently, you can evaluate the statistical significance of your lift! This is something I uncovered only two years ago. I guess this makes sense as it's pointless to have a high lift if your sample size is too small to give one confidence for generalizability, and the statistical test below will let you know if your lift is meaningful.

χ 2 = n*(lift − 1)² * supp * conf / ((conf − supp)*(lift − conf)) 

You'd then match the chi-square value calculated to the corresponding critical value in your usual probability distribution function lookup for hypothesis testing. You can use scipy.stats.chi2 to do this. There is no function I'm aware of that allows you to just feed in your usual variables, or in this case, lift, support and confidence, to obtain this as this is a fairly new and apparently still rather obscure invention.

Next, let's not forget the second and possibly even more important consideration in association rules. The ultimate goal is probably to increase sales revenue, so no matter how big or statistically significant your lift, if the overall observed frequency of items in your basket is still too small, you may not have enough purchases, and thus, revenue, to warrant launching the cross-sell campaign.
