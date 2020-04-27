# hello-world
just new thing
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv('data.csv')
data=data.groupby('Country/Region').sum()
data=data.iloc[:,2:]
data.head()

#date = pd.to_datetime(data.columns[0]).strftime('%Y-%m-%d')
#values=list(data.iloc[:,0].sort_values()[-5:])
#countries = list(data.iloc[:,0].sort_values()[-5:].index)
#plt.barh(countries,values)
#plt.title(date)
#plt.xlabel('Confirmed Number')
#plt.show()

from matplotlib.animation import FuncAnimation

def animate(i):
    date = pd.to_datetime(data.columns[i]).strftime('%Y-%m-%d')
    countries = list(data.iloc[:,i].sort_values()[-5:].index)
    values = list(data.iloc[:,i].sort_values()[-5:])
    plt.cla()
    plt.barh(countries,values,color=['pink','black','green','blue','chocolate'])
    plt.title(date)
 
plt.figure(figsize=(20,15))
ani = FuncAnimation(plt.gcf(),animate,interval=1000,frames=len(data.columns))
plt.show()
