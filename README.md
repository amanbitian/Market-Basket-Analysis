# Market-Basket-Analysis (MBA)
What is MBA ?
> It is a modeling technique based on the theory that **if u buy a certain group of items u are more likely to buy another group of items**  
> *Purpose of doing MBA is to determine what items customer purchase together*  
> `This implies we are more intrested in knowing about the products which are brought together`

### How does retail makes profit though this?
> Analyse what combination of product makes sense. like if I buy thoothpaste I am more likely to buy tooth brush with it, bread - butter/jam etc.
> The reason analyst wanna know this is because ***If I want to impliment a promotion I do like to know that if I discount an item how many other items are likely customers to buy. `This allow me to discount 1 product but more than make up on this discount by making sure the customers are picking baskets or combination of products they are profitable and make sense for me as an retailer`***

### What Applications of MBA?
1. Retail/supply Markets/ FMCG Companies
2. Insurance Companies
3. Medical
4. Bank/ Credic Card Companies
5. Telecom Analyse Various Services offered by Telecom Companies and what customers are purchasing

## Association Rules:

Association Rules are widely used to analyze retail basket or transaction data, and are intended to identify strong rules discovered in transaction data using measures of interestingness, based on the concept of strong rules.

![photo_2022-01-24_12-19-35](https://user-images.githubusercontent.com/86042628/150735635-d8139de6-fa81-438e-a756-16237ce693cc.jpg)

![Association rule MBA](https://user-images.githubusercontent.com/86042628/150663391-a86fc7b7-0070-4114-90d7-1fb74f15f707.png)


An example of Association Rules
* Assume there are 100 customers
* 10 of them bought milk, 8 bought butter and 6 bought both of them.
* bought milk => bought butter
* support = P(Milk & Butter) = 6/100 = 0.06
* confidence = support/P(Butter) = 0.06/0.08 = 0.75
* lift = confidence/P(Milk) = 0.75/0.10 = 7.5
Note: this example is extremely small. In practice, a rule needs the support of several hundred transactions, before it can be considered statistically significant, and datasets often contain thousands or millions of transactions.

## Advantages of Market Basket Analysis

MBA helps retailers with:

* Increases customer engagement
* Boosting sales and increasing RoI
* Improving customer experience
* Optimize marketing strategies and campaigns
* Help to understand customers better
* Identifies customer behavior and pattern

# What is the Difference between Association and Recommendation
Association rules ***do not extract an individual's preference***, `rather find relationships between sets of elements of every distinct transaction`. This is what makes them different than Collaborative filtering which is used in recommendation systems.  
Now to be very frank Market Basket Analysis is stupid simple. It really is: you’re effectively just looking at the likelihood of different elements occurring together. There’s more to it than that, but that’s the basis of this technique. We’re really just interested in learning how often things go together and how to predict when things will go together.
### Below is snap from amazon is example of association

![example of association](https://user-images.githubusercontent.com/86042628/150664527-0e3c8d13-a5a9-429f-896d-1f5899a73c8f.jpg)

## Apriori Algorithm
 
Apriori algorithm assumes that any subset of a frequent itemset must be frequent. Its the algorithm behind Market Basket Analysis.

Say, a transaction containing {Grapes, Apple, Mango} also contains {Grapes, Mango}. So, according to the principle of Apriori, if {Grapes, Apple, Mango} is frequent, then {Grapes, Mango} must also be frequent.

## Limitation of Apriori algorithm
 
Frequent Itemset Generation is the most computationally expensive step because the algorithm scans the database too many times, which reduces the overall performance. Due to this, the algorithm assumes that the database is Permanent in the memory.

Also, both the time and space complexity of this algorithm are very high: O(2^{|D|}), thus exponential, where |D| is the horizontal width (the total number of items) present in the database.

 ![optimizing apriori](https://user-images.githubusercontent.com/86042628/150664573-ccdab4ee-7421-401f-b247-879def8b8d61.png)
 
 Transaction reduction

We can optimize the existing apriori algorithm by which it will take less time and also works with less memory using these methods:

* **Hash-based itemset counting:** A k-itemset whose corresponding hashing bucket count is below the threshold cannot be frequent.
* **Transaction reduction:** A transaction that does not contain any frequent k-itemsets useless in subsequent scans.
* **Partitioning:** An itemset that is potentially frequent in DB must be frequent in at least one of the partitions of DB.
* **Sampling:** Mining on a subset of given data, lower support threshold + a method to determine the completeness.
* **Dynamic itemset counting:** add new candidate itemsets only when all of their subsets are estimated to be frequent.
