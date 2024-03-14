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

## Results

Using the pyfopt library we are going to get the best proportion of each stock that resulted the maximum sharpe ratio.

```
# Get the expected returns and covariance matrix
mu = expected_returns.mean_historical_return(df)
S = risk_models.sample_cov(df)

# optimize for max sharpe ratio
ef = EfficientFrontier(mu, S)
weights = ef.max_sharpe() # maximizing sharpe ratio, how much the return increase in every risk increase
cleaned_weights = ef.clean_weights() # rounding some near zero weights
print(cleaned_weights)

# print portofolio allocation
ef.portfolio_performance(verbose=True)
```

We get this output
```
OrderedDict([('UNVR.JK', 0.0), ('BRIS.JK', 0.49753), ('ASII.JK', 0.23315), ('TLKM.JK', 0.1236), ('BSSR.JK', 0.14572)])
Expected annual return: 24.0%
Annual volatility: 21.4%
Sharpe Ratio: 1.03
```

The Sharpe ratio we calculated (1.0) is significantly better than the previous value (0.6). While it still falls within the “adequate” range, it indicates a stronger return relative to the risk involved.

To achieve this improved Sharpe ratio, we recommend investing in the following proportions:

- BRIS: 50%
- ASII: 23%
- TLKM: 12%
- BSSR: 15%
UNVR is excluded due to its previously calculated negative returns, which would negatively impact the portfolio’s overall performance.

Now, let’s consider how to allocate a specific investment amount, say IDR 10 million, to maximize returns based on this Sharpe ratio.

```
# Get the discrete allocations for each share with amount of money available
from pypfopt.discrete_allocation import DiscreteAllocation, get_latest_prices

latest_prices = get_latest_prices(df) # get latest price of each stocks
weights = cleaned_weights
da = DiscreteAllocation(weights, latest_prices, total_portfolio_value= 10000000)

allocation, leftover = da.lp_portfolio()
print('Discrete allocation:', allocation)
print('Funds remaining: Rp {:.2f}'.format(leftover))
```

```
Discrete allocation: {'BRIS.JK': 2861, 'ASII.JK': 412, 'TLKM.JK': 313, 'BSSR.JK': 389}
Funds remaining: Rp 1988.13
```

Based on the calculated allocation and with a starting capital of IDR 10 million, here’s the recommended breakdown of our portfolio:

- BRIS: 2,861 shares
- ASII: 412 shares
- TLKM: 313 shares
- BSSR: 389 shares
This allocation maximizes your portfolio’s return potential based on the Sharpe ratio. It’s important to note that due to potential fractional share limitations by some brokerages, you might end up with a slightly different number of shares and a small remaining cash balance which is IDR 1988.13.

