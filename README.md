# Project-02
## Files
### mdb_populate_binance.ipynb
Populates the database with selected coin pairs and Fear and Greed Index, uses an already set up Mongo Database to store the data.
**Suggested to run only if we need new data loaded into the db**

### mdb_update_binance.ipynb
Updates the database with the configured data to the last minute. 
**Suggested to run only if we need up-to-date data loaded into the db, this update will change the data and therefore might show different results in the predictions every time an algo is run**

### model_selector.ipynb
Runs severals Finta indicators and and several SKLearn Algorithms to show which one is more accurate.
**Main file to run to do some testing**

## Pending
- [ ] Add Coin Pair to DB list when "populate"
- [x] Add Feature Importances (https://towardsdatascience.com/understanding-feature-importance-and-how-to-implement-it-in-python-ff0287b20285)
- [ ] Add Google Trends
- [ ] Backtest the Returns etc
- [ ] Improve features (test more finta etc)
- [ ] Find the best Coinpair (highest accuracy) to focus on
- [ ] Export the best model to the DB, to be used in UI for "live" predictions
- [ ] Ensemble Machine Learning: Add some more (https://scikit-learn.org/stable/modules/ensemble.html)

## Packages
!pip install pandas numpy pymongo==4.0.0 python-binance dnspython python-dotenv pytrends