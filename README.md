# Top IHSG Stocks Portofolio Optimization using Sharpe Ratio Maximization
This project will demonstrate several IHSG stocks portofolio optimization using Sharpe Ratio Maximization method.

## Background
Sharpe Ratio is a one of the simpliest methods in portofolio analysis. This method simply adjust the portofolio return to the free-risk portofolio return and compare it to the risk of the portofolio itself. So basically the Sharpe Ratio measure how many returns of the portofolio above the free-risk portofolio in each of the risk unit increase. 

In mathematical language :

__Returns (R)__ : the average annual (or certain period) returns of each portofolio (in this context stocks portofolio)

__Risks (σ)__ : the standard deviation (square root of variance) of each portofolio values (in this context stocks portofolio)

$$
Sharpe Ratio = \frac{(R_p - R_f)}{\sigma_p}
$$

Where:
- _Rp_ : Expected return of the portfolio
- _Rf_ : Risk-free rate of return (e.g., government bond yield)
- _σp_ : Standard deviation of the portfolio's returns (measure of volatility or risk)

So in this project, we want to maximize our pre-defined stocks portofolio from Indonesian stocks (UNVR, BRIS, ASII, TLKM, BSSR) using sharpe ratio maximization method that is basically only using these two concepts in statistics : mean and variance. Assuming that we have 10 millions IDR cash in hand and want to invest in those stocks. In order to maximize our return and minimize risk, using the method, we can obtain how much money should we invest in each stocks.


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