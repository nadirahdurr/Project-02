# Project-02
### mdb_populate_binance.ipynb
Populates the database with selected coin pairs and Fear and Greed Index, uses an already set up Mongo Database to store the data.
**Suggested to run only if we need new data loaded into the db**

### mdb_update_binance.ipynb
Updates the database with the configured data to the last minute. 
**Suggested to run only if we need up-to-date data loaded into the db, this update will change the data and therefore might show different results in the predictions every time an algo is run**

### model_selector.ipynb
Run severals Finta indicators and and several SKLearn Algorithms to show which one is more accurate.
**Main file to run to do some testing**