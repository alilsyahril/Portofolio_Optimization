# Top IHSG Stocks portfolio Optimization using Sharpe Ratio Maximization
This project will demonstrate several IHSG stocks portfolio optimization using Sharpe Ratio Maximization method.

## Background
Sharpe Ratio is a one of the simpliest methods in portfolio analysis. This method simply adjust the portfolio return to the free-risk portfolio return and compare it to the risk of the portfolio itself. So basically the Sharpe Ratio measure how many returns of the portfolio above the free-risk portfolio in each of the risk unit increase. 

In mathematical language :

__Returns (R)__ : the average annual (or certain period) returns of each portfolio (in this context stocks portfolio)

__Risks (σ)__ : the standard deviation (square root of variance) of each portfolio values (in this context stocks portfolio)

$$
Sharpe Ratio = \frac{(R_p - R_f)}{\sigma_p}
$$

Where:
- __Rp__ : Expected return of the portfolio
- __Rf__ : Risk-free rate of return (e.g., government bond yield)
- __σp__ : Standard deviation of the portfolio's returns (measure of volatility or risk)

So in this project, we want to maximize our pre-defined stocks portfolio from Indonesian stocks (UNVR, BRIS, ASII, TLKM, BSSR) using sharpe ratio maximization method that is basically only using these two concepts in statistics : mean and variance. Assuming that we have 10 millions IDR cash in hand and want to invest in those stocks. In order to maximize our return and minimize risk, using the method, we can obtain how much money should we invest in each stocks.


## Setup
install all the requirement libraries in the requirements_portopt.txt using command :
```
pip install -r requirements_portopt.txt
```

We suggest the reader to use a dedicated virtual environment when working on this project to avoid any mismatching library version during install. So before installing all the requirements, make the virtual environment using these following commands :
```
## make the dedicated venv
python -m venv your_project_name

## to enter the venv
source your_project_name/bin/activate
```