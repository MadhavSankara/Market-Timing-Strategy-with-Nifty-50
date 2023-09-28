# Market-Timing-Strategy-with-Nifty-50
A combination of macro and market related factors are taken to check their relationship with Nifty 50's returns. The data is taken from 1 Jan 2013 to 1 Jan 2023. The macro data is mostly taken from FRED and the market data is from Nifty indices except the CAPE ratio which is from Barklays.
# Model
A linear regression time series model is built by regressing nifty forward returns with the other parameters. The variable forms for the parameters are modified after seeing the plot. If any trend is observed, then the difference is considered. Log of the parameters is considered to mitigate the effect of large fluctuations, especially because 2020 is included. In instances where the absolute value of the independent variable is large, z-scores have been used. Because most of the independent variables have been seasonally adjusted, no seasonal adjustment has been made. 
Also no auto-regresion has been considered, although an ARIMAX model would be more suited for the purpose. 
Also resampling was done for data which had a frequency of less than daily.
Ideally, some degree of smoothing(like a moving average) should be made for the independent variables, but hasn't been made as that would reduce the time horizon available for building the model. 
# Dimensionality Reduction
A simple correlation table was constructed to see, which independent variable(X) were highly correlated to anti-correlated with the dependent variable(Y). A model was built using all the X's and another was built using only the ones with correlation greater than 0.1 or lesser than -0.1. This resulted in only 8 of the 15 Xs being used.
# Fitting the model
A linear regresion  model was fit using scikitlearn. The available data was split into training and testing data and the model was estimated resulting in a very low mean square error. 
# Market timing strategy and backtesting
A simple market timing model was constructed, where the 1 week forward returns for the model were considered. if it was > 0,stay invested; if 1 week forward returns < 0, move to cash (Cash returns haven't been considered; ideally they should be considered for better results).
This strategy was back tested within the same time period (ideally it should be tested out of sample, which is a drawback). The weekly values of both the invesment strategies are tabulted and plotted, i.e. buy and hold and market timing. The results of both the strategies are also given at the, including CAGR, Sharpe and Max Drawdown.
# Conclusion
This is a very rudimentary model, where more detail can be added. Log returns can be considered, variable smoothing should be done. Ideally more variables should be considered but public sources have limitations. The model, need note be linear, but atleast an ARIMAX should be considered. Machine learning models like STLT are available and the next set of models will be done using machine learning models. Finally the trading strategy can be further detailed, like considering cash, transaction costs, and also providing the option to go short the nifty.
