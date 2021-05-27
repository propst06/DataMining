import pandas as pd

scientists = pd.read_csv('https://raw.githubusercontent.com/chendaniely/\
pandas_for_everyone/master/data/scientists.csv')
#import dataset

scientists

born_datetime = pd.to_datetime(scientists['Born'], format='%Y-%m-%d')

born_datetime
#convert column 'Born' from object to datetime

scientists['born_dt'] = born_datetime

scientists
#create new column named born_dt with new dtype

scientists['oldest'] = scientists.iloc[0,1]

scientists
#pick oldest scientists birthdate and create new column

oldest_dt = pd.to_datetime(scientists['oldest'], format='%Y-%m-%d')

oldest_dt
#convert column oldest from object to datetime

scientists['oldest_dt'] = oldest_dt

scientists
#create new column named oldest_dt with new dtype

scientists.dtypes
#make sure the dtype matches before subtracting them 

scientists['Difference'] = scientists['oldest_dt'] - scientists['born_dt']
scientists
#create new column Difference to show the number of days difference between the birthdays of the oldest scientist and the rest of them

scientists ['Difference in Months'] = (scientists['Difference']/30.417)
scientists
#create new column Difference in Months to show the difference in birthdays by months. Used 30.417 because that is the standard when converting days into Months. 

scientists = scientists.drop(['oldest', 'Born'], axis=1)

scientists
#dropped columns Born and oldest in order to clean up the dataset

from google.colab import drive
drive.mount('/drive')

scientists.to_csv('/drive/My Drive/Colab Notebooks/KaitlynPropstAssignment2DataMining')
#converted to csv file.
