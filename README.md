# Application of Bayesian update for data credibility assurance
This is an idea to apply Bayesian update concept for data credibility measurement. 

## Motivation
In a tech-company I was working for before, I was responsible for data quality amalysis and improvement. They were developping an AI service for business intelligence, and they were collecting information about all kinds of companies all over the world for their product. One of the biggest issues for them was data quality or credibility more precisely, since they were relying on data scraping from random business related webpages for company data. That is, when their data scrapin system collected data about companies, there was no gurantee that these informations were correct. For example, suppose that in our database we have a several entities of the headquarters location of Amazon scraped from various types of websites, sometimes these data do not agree to one another, such as some sources saying Califorlia but others saying New York. My question was if some sort of objective metric could be established to evaluate how much we can trust certain data. Since their service was to provide company information and automated analysis, this was a crucial challenge for them.

## Bayes Theorem and Bayesian Updating
### Conditional probability
Conditional probability is probability of a certain event occurring given that another certain event has occurred.
Probability of event A conditioned on B is denoted by P(A|B). Be aware of joint probability P(A,B), which is the probability of two events A and B occur together. Definition is:

<img src="https://render.githubusercontent.com/render/math?math=P(A|B) = \frac{P(A,B)}{P(B)}">
