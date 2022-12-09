# MORE hackathon @ Athena RC


## Description

In this repository you can find a library with a variety of functionalities related to performing advanced analytics on time-series data from Renewable Energy Sources (RES). In particular, in “forecast_example.ipynb”, you can see an example of putting some of those functionalities in action in order to forecast the power output of a wind farm. We apply some initial preprocessing of the data such as scaling, removal of outliers, handling of missing values, etc. Then, we try to forecast the hourly minimum power of the park for 48-hours in the future. To do this, we have modeled the problem as a regression task where each data vector contains the current values of relevant variables, past (“lagged”) values of the variables, as well as any available information for every hour in the future (e.g., numerical weather forecasts). The target of the regression task is the minimum power production of the next hour in the future and then in an autoregressive manner using the data vector along with the forecast of the 1st hour in the future to predict the 2nd hour and so on (we are using sklearn’s RegressorChain for this). Finally we evaluate our models in a test set we have kept separate by using metrics such as mean average percentage error (MAPE), root mean squared error (RMSE) and mean absolute error (MAE).



## Installation

- Clone the repository

```shell

git clone https://github.com/MORE-EU/more_api.git
```

- Get into the repository you just cloned

```shell
cd hackathon_athena
```

- Install the dependancies

```shell
pip install -r requirements.txt
```

- Run a jupyter lab server that listens on the specified port 

```
jupyter lab --no-browser --port=<port>
```

## Task

Your task for this hackathon is to use the provided example as base and try to solve a forecasting problem for a solar panel. More specifically, you will focus on forecasting the hourly average power output of the panel for 24-hours ahead. For this task, you will use an open dataset from NREL that you can find at https://datahub.duramat.org/dataset/data-for-validating-models-for-pv-module-performance. To evaluate your models keep the last 2 months of the dataset as the test set. Finally, create some plots to graphically demonstrate your results.



Some hints:

- You can find some code on how to parse the NREL dataset in “read_soiling_data.ipynb”.

- Consider resampling your dataset in a lower granularity.

- Since solar panels are dependent on the sunlight there are daily (and possibly weekly, monthly, etc.) repeating patterns in the sunlight strength. Try to incorporate that information in your models.

- Try to think which variables are the most correlated to the current and possibly the future value of the active power of the solar panel.

- You will need a way to decide which “lagged” values are more correlated to the current ones. Are there measures that help you calculate this ?
