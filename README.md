# Web Traffic Time Series Forecasting

Forecast future traffic to Wikipedia pages

## Getting Started

This Project is about predicting the future behaviour of time series’ that describe the web traffic for Wikipedia articles. The data contains about 145k time series and comes in two separate files: train_1.csv, train_2.csv holds the traffic data, where each column is a date and each row is an article, and key_1.csv , key_2.csv contains a mapping between page names and a unique ID column (to be used in the submission file).

### Prerequisites

What things you need to install the software and how to install them

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import re
%matplotlib inline
from statsmodels.tsa.arima_model import ARIMA
import warnings
```

### Installing

A step by step series of examples that tell you have to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo


## Deployment

I. Importation & Data Cleaning
II. Aggregation & Visualisation
III. Machine Learning Approach
IV Median of Medians Model Approach
V. ARIMA approach (Autoregressive Integrated Moving Average)
VI. Comparaison & Conclusion

### Importation & Data Cleaning
### Aggregation & Visualisation
### Median of Medians Model Approach
### ARIMA approach (Autoregressive Integrated Moving Average)
ARIMA stands for Autoregressive Integrated Moving Average.
The ARIMA model combines three basic methods:
 ```  
AutoRegression (AR) – In auto-regression the values of a given time series data are regressed on their own lagged values, which is indicated by the “p” value in the model.
    
Differencing (I-for Integrated) – This involves differencing the time series data to remove the trend and convert a non-stationary time series to a stationary one. This is indicated by the “d” value in the model. If d = 1, it looks at the difference between two time series entries, if d = 2 it looks at the differences of the differences obtained at d =1, and so forth.
Moving Average (MA) – The moving average nature of the model is represented by the “q” value which is the number of lagged values of the error term.
```

This model is called Autoregressive Integrated Moving Average or ARIMA(p,d,q) of Yt.  We will follow the steps enumerated below to build our model.

Step 1: Testing and Ensuring Stationarity

To model a time series with the Box-Jenkins approach, the series has to be stationary. A stationary time series means a time series without trend, one having a constant mean and variance over time, which makes it easy for predicting values.

Testing for stationarity – We test for stationarity using the Augmented Dickey-Fuller unit root test. The p-value resulting from the ADF test has to be less than 0.05 or 5% for a time series to be stationary. If the p-value is greater than 0.05 or 5%, you conclude that the time series has a unit root which means that it is a non-stationary process.

Differencing – To convert a non-stationary process to a stationary process, we apply the differencing method. Differencing a time series means finding the differences between consecutive values of a time series data. The differenced values form a new time series dataset which can be tested to uncover new correlations or other interesting statistical properties.

We can apply the differencing method consecutively more than once, giving rise to the “first differences”, “second order differences”, etc.

We apply the appropriate differencing order (d) to make a time series stationary before we can proceed to the next step.

Step 2: Identification of p and q

In this step, we identify the appropriate order of Autoregressive (AR) and Moving average (MA) processes by using the Autocorrelation function (ACF) and Partial Autocorrelation function (PACF).  Please refer to our blog, “Starting out with Time Series” for an explanation of ACF and PACF functions.

Identifying the p order of AR model

For AR models, the ACF will dampen exponentially and the PACF will be used to identify the order (p) of the AR model. If we have one significant spike at lag 1 on the PACF, then we have an AR model of the order 1, i.e. AR(1). If we have significant spikes at lag 1, 2, and 3 on the PACF, then we have an AR model of the order 3, i.e. AR(3).

Identifying the q order of MA model

For MA models, the PACF will dampen exponentially and the ACF plot will be used to identify the order of the MA process. If we have one significant spike at lag 1 on the ACF, then we have an MA model of the order 1, i.e. MA(1). If we have significant spikes at lag 1, 2, and 3 on the ACF, then we have an MA model of the order 3, i.e. MA(3).

Step 3: Estimation and Forecasting

Once we have determined the parameters (p,d,q) we estimate the accuracy of the ARIMA model on a training data set and then use the fitted model to forecast the values of the test data set using a forecasting function. In the end, we cross check whether our forecasted values are in line with the actual values.



## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone who's code was used
* Inspiration
* etc

