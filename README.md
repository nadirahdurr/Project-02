# getcryptorich.com
​
### This is a tool that aims to develop a crypto trading tool that compares the accuracy and hypothetical returns of multiple machine-learning model types and time periods for a chosen crypto pair with the intent of optimizing crypto trading algorithms.
​
The main research question we wanted to explore was what is the most optimal model and timeframe to use to trade a chosen crypto coin?
​
- Disclaimer: the content contained in this project is for informational purposes only and should not construe any such information as investment, financial, tax, legal or other advise. Any ideas or strategies discussed herein should not be undertaken by any individual without prior consultation with a financial professional for the purpose of assessing whether the ideas or strategies that are discussed are suitable to you based on your own personal financial objectives, needs and risk tolerance.
​
---
​
## Technologies
​
This project leverages python 3.9 and Google Colab was used to run all analysis.
​
We used the following tools to gather information:
​
- [Binance API](https://www.binance.com/en/support/faq/c-6?navId=6) - this method allows you to connect to the Binance servers via Python to automate your trading and pull live financial data.
- [MongoDB](https://www.mongodb.com/) - this is a document database used for high volume data storage.
​
---
​
## Installation Guide
​
Before running the application first import the following libraries and dependencies.
​
```python
!pip install pandas
!pip install numpy
!pip install pymongo==4.0.0
!pip install dnspython
​
import pandas as pd
import numpy as np
import hvplot.pandas
import os
import pickle
from pathlib import Path
from datetime import datetime
from pymongo import MongoClient
from pprint import pprint
from dotenv import load_dotenv
from pandas.tseries.offsets import DateOffset
from finta import TA
​
For training and testing data:
from sklearn.preprocessing import StandardScaler
from imblearn.over_sampling import RandomOverSampler
​
Import the classifier Models
from sklearn.svm import SVC
from sklearn.tree import DecisionTreeClassifier
from sklearn.neural_network import MLPClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.gaussian_process import GaussianProcessClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.gaussian_process.kernels import RBF
from sklearn.ensemble import RandomForestClassifier, AdaBoostClassifier, BaggingClassifier
from sklearn.discriminant_analysis import QuadraticDiscriminantAnalysis
​
Import Classification Report
from sklearn.metrics import classification_report
​
```
​
---
​
## Data Preparation
​
The `utils` folder contains the nine functions utilized in the file `model_selector.ipynb`, which runs the selected Finta indicators and the SKLearn Algorithms to show the optimal model or each timeframe indicated per cryptocurrency coin pair.
​
**9 Crypto coin pairs**:
ADABUSD, SOLBUSD, DOGEBUSD, MATICBUSD, MANABUSD, SHIBBUSD, ETHBUSD, LUNABUSD, BTCBUSD
​
**4 Timeframes**: 30m, 1h, 4h, 1d
​
**27 Indicators tested**:
DMI+, DMI-, MOBO Upper, MOBO Middle, MOBO Lower, SMA Fast, SMA Medium, SMA Slow, SSMA, EMA20, EMA50, EMA200, DEMA, TRIMA, WMA, RSI, STOCHRSI, MACD, VW MACD, KAMA, ZLEMA, PZO, MFI, SQZM, Fear and Greed, Google Trends, Volume
​
**12 Models**:
RandomForestClassifier, SVM, SVM linear, DecisionTreeClassifier, AdaBoostClassifier, AdaBoostClassifier 5000, MLPClassifier, GaussiaNB, GaussianProcessClassifier, KNeighborsClassifier, KNeighborsClassifier_3, KNeighborsClassifierBagging
​
---
​
## Results
​
The combination of the following 13 indicators consistently produced the highest model accuracy for each of the chosen coin pairs and models:
SMA Fast, SMA Slow, SSMA, EMA20, EMA50, DEMA, TEMA, TRIMA, WMA, STOCHRSI, F&G, Google Trends, Volume
​
Below is a sample chart displayed on MongoDB:
​
![All Coins Accuracy](Images/All_Coins_Accuracy.png)
​
Below is a summary of the best model and timeframe to use per coin we chose:
​
- ADABUSD
​
  - Model:
  - Timeframe:
​
- BTCBUSD
​
  - Model:
  - Timeframe:
​
- ETHBUSD
​
  - Model:
  - Timeframe:
​
- SOLBUSD
​
  - Model:
  - Timeframe:
​
- LUNABUSD
​
  - Model:
  - Timeframe:
​
- DOGEBUSD
​
  - Model:
  - Timeframe:
​
- MATICBUSD
​
  - Model:
  - Timeframe:
​
- MANABUSD
​
  - Model:
  - Timeframe:
​
---
​
## Conclusion
​
For users to view a summary of all the coin pairs, they can visit [this website](https://project-2-liard.vercel.app/) to get an understanding of which model and timeframe to select for the coin they wish to trade for optimal profits.
​
Although we have identified certain indicators, models, and timeframes to be optimal for trading certain coins, it is still important to also look at the rist metrics associated with each coin.
​
This site we created also includes financial risk metrics, such as annual volatility, annualized return, cumulative returns, the Sharpe ratio, and the Sortino ratio for the user to reference and make the best financial decisions.
​
## From Gabriel's original ReadMe:
​
### populate_database.ipynb:
​
Populates the database with selected coin pairs and Fear and Greed Index, uses an already set up Mongo Database to store the data.
**Suggested to run only if we need new data loaded into the db**
​
### update_database.ipynb
​
Updates the database with the configured data to the last minute.
**Suggested to run only if we need up-to-date data loaded into the db, this update will change the data and therefore might show different results in the predictions every time an algo is run**
​
## Pending
​
- [ ] Add Coin Pair to DB list when "populate"
- [x] Add Feature Importances (https://towardsdatascience.com/understanding-feature-importance-and-how-to-implement-it-in-python-ff0287b20285)
- [ ] Add Google Trends
- [ ] Backtest the Returns etc
- [ ] Improve features (test more finta etc)
- [ ] Find the best Coinpair (highest accuracy) to focus on
- [ ] Export the best model to the DB, to be used in UI for "live" predictions
- [ ] Ensemble Machine Learning: Add some more (https://scikit-learn.org/stable/modules/ensemble.html)