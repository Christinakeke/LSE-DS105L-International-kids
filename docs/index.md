<div>
   <center>
        <b>
            <font color="34,63,93" size="7">
                SOOOO expensive!💰
            </font>
        </b>
    </center>
</div>

<div>
   <center>
        <b>
            <font color="34,63,93" size="4">
                A study of the exchange rate and inflation rate of the top 10 GDP countries
            </font>
        </b>
    </center>
</div>

<div>
   <center>
        <font color="black" size="3">
                Ke Chen, Yujia Zhu, Maggie Miao
        </font>
    </center>
</div>>
***

## 📝 Project Description


## 📊 Data
### Data Source
#### Exchange rate:
We collecet our exchange rate data by using the exchange rate API. We use this API to collect exchange rate data of top 10 GDP countries from 2013 to 2022. 
```python
import requests
import pandas as pd

def get_exchange_rates(base_currency):
    url = "https://api.apilayer.com/exchangerates_data/timeseries"
    headers = {
        "apikey": "We love data science!"
    }
    rates = {}
    year = pd.Timedelta(days=365)
    query_date = pd.to_datetime('2022-12-31')
    while query_date >= pd.to_datetime('2013-12-31'):
        # Set the start and end dates for the current year
        current_year_start = (query_date - year).strftime('%Y-%m-%d')
        current_year_end = query_date.strftime('%Y-%m-%d')
        params = {'access_key': 'xG4VP7WvDuXtP5HxdzfyHmPw0rR4Ymza',
                  'start_date': '2013-12-31',
                  'end_date': '2022-12-31',
                  'base': base_currency,
                  'symbols': 'USD'}
        try:
            response = requests.get(url, params=params, headers=headers)
            response.raise_for_status()
            data = response.json()
            rates.update(data['rates'])
        except requests.exceptions.RequestException as e:
            print("Error: ", e)
        query_date -= year
    # Create a DataFrame from the rates dictionary
    df = pd.DataFrame.from_dict(rates, orient='index')
    return df
```

#### Inflation rate:
For inflation rate, we used static data from OECD website. We collected inflation rate data of top 10 GDP countries from 2013 to 2022. <br/>
[OECD website](https://data.oecd.org/price/inflation-cpi.htm)

2. Inflation rate:
### Data Pre-Processing
## 📈 Analysis

## 🖼️ Results

## 🖋️ Conclusions

## 📚 References
