# Application of Bayesian update for data credibility assurance
This is an idea to apply Bayesian update concept for data credibility measurement. 

## Motivation
In a tech-company I was working for before, I was responsible for data quality amalysis and improvement. They were developping an AI service for business intelligence, and they were collecting information about all kinds of companies all over the world for their product. One of the biggest issues for them was data quality or credibility more precisely, since they were relying on data scraping from random business related webpages for company data. That is, when their data scrapin system collected data about companies, there was no gurantee that these informations were correct. For example, suppose that in our database we have a several entities of the headquarters location of Amazon scraped from various types of websites, sometimes these data do not agree to one another, such as some sources saying Califorlia but others saying New York. My question was if some sort of objective metric could be established to evaluate how much we can trust certain data. Since their service was to provide company information and automated analysis, this was a crucial challenge for them.

## Bayes Theorem and Bayesian Updating
### Conditional probability
Conditional probability is probability of a certain event occurring given that another certain event has occurred.
Probability of event A conditioned on B is denoted by P(A|B). Be aware of joint probability P(A,B), which is the probability of two events A and B occur together. Definition is:

<img src="https://render.githubusercontent.com/render/math?math=P(A|B) = \frac{P(A,B)}{P(B)}">

### Bayese Theorem
From the above definition and commutativity of joint probability P(B,A) = P(A,B)

<img src="https://render.githubusercontent.com/render/math?math=P(A|B) = \frac{P(A,B)}{P(B)} = \frac{P(B|A)P(A)}{P(B)}">

This is called Bayes Theorem.

### Bayesian updating
Bayesian approach sees probability as observer's confidence (subjective probability), and put Bayes Theorem as the basis for all calculation. According to Bayesian Inference, one has a current state of confidence (a priori/prior probability), and then update his confidence everytime he achieves new information (Data). The updated confidence is called a posteriori/posterior probability, and this process is called Bayesian updating.
Now given that we have a certain hypothesis H in our mind with a priori probability P(H), we update our confidence upon a new data D to a posteriori probability P(H|D) according to Bayes Thorem:

<img src="https://render.githubusercontent.com/render/math?math=P(H|D) = \frac{P(D|H)P(H)}{P(D)}">

Here the conditional probability P(D|H) on the right hand side is likelihood of data D when hypothesis H is true. The denominator P(D) is the total probability of data D occuring for all scenarios. That is, it is calculated as

<img src="https://render.githubusercontent.com/render/math?math=P(D) = P(D|H)P(H) + P(D|\neg H)P(\neg H)">

## Application of Bayesian updating to data credibility assurance
We can apply this method to evaluate how much we can trust our data, especially those simple and categorical, e.g. headquarters, founded year.

To sum up our situation, we have a certain information (e.g. HQ) for some company (e.g. "Amazon") from a few sources (e.g. webpage of a startup event, business news, company's official website). Since any source is not 100% reliable and our scraper does't always work accurately, we are not sure if the obtained information is correct. And the biggest problem is, sometimes (often) they do not agree to one another (e.g. for HQ of AtomLeap, source A says "California", whereas source B says "New York").

Suppose that we know the probability of each source giving correct information (the central part of this project, we will come back to this later), this probability can be used as the likelihood P(D|H) in Bayesian updating formula. If we obtain a certain information $H$ from a source with 90% accuracy, then we start with a priori probability P(H) = 90. Then everytime we get a new data from different sources, depending whether it agrees with it or not, we update our confidence for this hypothesis H based on the Bayesian formula.
