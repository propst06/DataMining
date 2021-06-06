
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
plt.style.use('classic')

df = sns.load_dataset("anscombe")
#Load dataset

print(df)
#Look at all dataset to see what information I want to draw from it 

df_1 = df[df['dataset'] == 'II']
#select two datasets from list

df_2 = df[df['dataset'] == 'IV']

plt.plot(df_1['x'], df_2['y'])
#plot using line graph

sns.set()

plt.plot(df_1['x'], df_2['y'])
#just wanted to see if sns.set() would change anything about the graph

sns.distplot(df_1['x'])
sns.distplot(df_2['y']);
#showing both a histogram and kernal density estimation to get a better visual of II and IV datasets

sns.pairplot(df, hue='dataset', size=2.5);
#showing entire anscombe dataset plotted as well as just a histogram of II and IV. 

Seaborn is best used when wanting to show meaningful graphics while exploring data, as it provides an API on top of matplotlib and it's integrated well with Pandas. It allows the user to focus on the data instead of making sure that the graphs themselves are usable. 
