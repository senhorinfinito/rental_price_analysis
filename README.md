# Rental Analysis - Pune:  Project Overview

![ViewCount](https://views.whatilearened.today/views/github/senhorinfinito/rental_price_analysis.svg?cache=remove)


* Secured a tool that estimates the rental price for Pune city which will help a person to estimates rent according to the parameters like comfort, location & many more. 
* Scrapped over 16000+ houses descriptions from 99acres.com using Python and  **Beautiful Soup**. 
* Generated features from total facilities provided by the owner, also created valuable features related cost from. 
* Engineered Geospatial features using text address data. 
* Optimised Linear, Random forest regressor using Randomsearchcv
* Built a client-facing API using flask. 

# Code & Resources used 

**Python Version:**  3.8 

**Packages:** Pandas, Scikit-learn, Numpy, Geocoder, Folium, BeautifulSoup, flask, JSON, pickle, Matplotlib, seaborn.

**For WebFrame requirements:** ```pip  install requirements.txt```

**rent Traffic:** Check map.html to check current rent traffic.

**Flask deployment Tutorial** - https://towardsdatascience.com/productionize-a-machine-learning-model-with-flask-and-heroku-8201260503d2

### Motivation
- DS Project from Scratch by Ken Jee -  https://www.youtube.com/playlist?list=PL2zq7klxX5ASFejJj80ob9ZAnBHdz5O1t
- #66daysofdata - https://www.youtube.com/watch?v=iiSZqsQKNX8&ab_channel=KenJee

# Web Scrapping 


This code helps you to find different house's data which is the available web. 

I referred to 99acres.com for this project. The interface of the web page looks like this:

![99acre.com](https://github.com/senhorinfinito/scrappers/blob/main/images/99acres.jpg)

Run the web scraper to scrape 15000 housing data from [99acres.com](https://www.99acres.com/flats-for-rent-in-pune-ffid-page-2) Each sample(row) has the following points:
- rent (Target Variable)
- Number of bedrooms
- Number of bathrooms 
- Number of Balconies 
- Brokerage amount 
- Deposit Amount 
- Maintenance amount
- Built-Up Area
- Super Built-Up Area
- Type of Furnishing
- Availability for 
- Address
- Floor Number 
- Home Facing
- Floor-type
- Gate Community
- Corner Property 
- Parking Count
- WheelChairFacility
- Pet-Friendly
- Agreement Duration
- Electricity Bill
- Power Backup  Facility
- Property age
 
# Data Cleaning 

After scrapping 16000+  data from the web. Data contained a large amount of text data combined with numerical data. I needed to clean it so that it was usable for the model for ML model. 


I performed few operations of data cleaning are listed below:
- Derived locality of address by cleaning text parameter. 
- Parsed numerical values from the area.
- Removed rows which doesn't value.
- Parsed facilities 4 features from a list of text data.
- Made cost-wise columns such as deposit(security amount), maintenance amount & brokerage amount from the text data list.
- Parking count has simplified, merged open & closed parking values.
- Parsed numeric data from agreement duration, notice durations.

# EDA 

I used folium & geocoder packages to create & analyze rent quantitative distribution area-wise in the city. 

**MAP Visual**


![map](https://github.com/senhorinfinito/rental_price_analysis/blob/main/images/map2.jpg)

**Continuous Data**

Also, Based on a list of the continuous data variables did bivariate.  
![categorical Variabels](https://github.com/senhorinfinito/rental_price_analysis/blob/main/images/continous_variables.jpg)
 
**Ordinal Varibale**

You can check the bivariate analysis of data for ordinal variables.
![bi-va-analysis](https://github.com/senhorinfinito/rental_price_analysis/blob/main/images/ordinal_variable.jpg)


## Model Building 

* Following step I have before building model 
* Used Binary Encoding for Binary variables
* Used Ordinal Encoding on Ordinal Variables 

I have 2 differnt models & evaulted them with using mean absolute error  & mean_log_squared_error. I chose MAE & MLSE for because it is easy to interpret. 

Model Listing : 
1. Linear Regression:  Create a baseline for model.
2. Random forest regressor: This model is selected due to good fitment on data.

Apart from that I use lasso & Ridge to check performace imporvement. But this part is not included in notebook. 


# Model Performace :
**Linear Regression :** r2_score : 0.69. 

**Random_forest :** r2_score : 0.98 on train data & ~0.90 on test data / MSLE is  0.23. 

# Productionization
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary.

# deployment

**This is a client-facing API using flask run into cmd**

To use please clone repository first in local enviroment.

Install requirements from  ```pip install -r requirements.txt```

```activate venv``` : activate env

```requests.py``` : contain the get request file.

```data_input```  :  Input file of requests.
