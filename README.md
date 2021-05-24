# DataMining
import pandas as pd

import io
import requests
url="https://data.medicaid.gov/api/views/mmgn-kvy5/rows.csv?accessType=DOWNLOAD"
s=requests.get(url).content
c=pd.read_csv(io.StringIO(s.decode('utf-8')))
#This was me experimenting with being able to download the file from the internet
df = pd.read_csv("https://data.medicaid.gov/api/views/mmgn-kvy5/rows.csv?accessType=DOWNLOAD", low_memory=False)
#this allowed the file to have usable colummns. I used low_memory because that's what the instructions said to do with this data.
df.head()
#prints the first five rows of the data
df.head(10)
#prints the first ten rows of the data
df.tail()
#prints last five rows of the data
df.tail(10)
#prints the last ten rows of the data
df.columns
#lists all of the columns in the dataset
type(df)
#tells us what kind of data is in the dataset
df.shape
#tells us how many rows and columns are in the data set
df.groupby(['State', 'Year'])[['Medicaid Amount Reimbursed', 'Non Medicaid Amount Reimbursed']].mean()
#lists the mean of Medicaid Amount Reimbursed and Non Medicaid Amount Reimbursed grouped by the State and the Year.
