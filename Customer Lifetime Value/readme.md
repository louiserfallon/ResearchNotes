# Predictive Customer Lifetime Value

A Predictive Customer Lifetime Value model estimates/predicts the total present value of the amount each customer will spend over the rest of their life, using information about their past transactions. Once this value has been calculated, it can be used to identify what characterises highly valuable customers, and can help retailers to target their customer engagement efforts (marketing, product design etc).

This is in comparison to "Historical" Customer Lifetime value, where you simply look at the amount of money a customer has already spent, and try and identify the drivers for this.

PCLV is often done using the Pareto/NBD Model or the BG/NBD that models customer behviour in two steps
* At every time period the customer flips a weighted coin to determine if they will stay being a customer or not - survivorship is estimated using the Beta Geometric distribution where each individual is modelled as having an individual propensity to "churn" at any time period, or the Pareto model. Both are linked to the poisson distribution of time between purchaes, but the BG is less computationally intensive.
* If the customer is not "dead" then they spend a - expenditure is estimated using the Gamma Gamma model (http://brucehardie.com/notes/025/) 

This model only needs the "frequency", "recency", and "monetary" features of a customer, but additional features can be used to "explain" the variation in the parameters for each individual, by having those parameters be estimated as a linear regression on the relevant features.

Another type of CLV is the 1-year CLV, which estimates the customer's spend over the next 1 year, or any other time period. This can be done using more classic regression techniques, and is less of a calculation and more of a prediction. This model can use many more input features than just RFM, but of course doesn't really live up to the "L" in CLV.

The seminal dataset for this is the CDNOW dataset (http://www.brucehardie.com/datasets/).

Included in this repo:

* CLV Estimation in Python
	* RFM exploration & visualisations
	* CLV calculation with the lifetimes package
	* CLV calculation with pymc3 directly
	* CLV estimation with pymc3 including covariates
	* Next-period estimation with ML methods


References:
* Motivation and Mathematics:
	* https://medium.com/swlh/how-to-estimate-the-value-of-your-customers-the-right-way-57c63fad093
	* https://www.researchgate.net/publication/237287176_Modeling_Customer_Lifetime_Value
	* http://brucehardie.com/papers/bgnbd_2004-04-20.pdf

* Python based tutorials
	* https://github.com/datascienceinc/pydata-seattle-2017/blob/master/lifetime-value/pareto-nbd.ipynb
	* https://github.com/datascienceinc/oreilly-intro-to-predictive-clv
	* http://benalexkeen.com/bg-nbd-model-for-customer-base-analysis-in-python/

* R based tutorials
	* https://cran.r-project.org/web/packages/BTYDplus/vignettes/BTYDplus-HowTo.pdf


Key terms:
CLV - Customer Lifetime Value
NBD - Negative Binomial Distribution
RFM - Recency, Frequency, Monetary