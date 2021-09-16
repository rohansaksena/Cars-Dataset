# Cars Dataset Project

This is another of my basic data analysis projects containing some data analysis and visualisation .
Here , a data of different cars is given with there specifications namely : Make, Model, Type, Origin, MSRP, Invoice, EngineSize, Cylinders, Horsepower, MPG_City, MPG_Highway, Weight, Wheelbase, Length. This Data is Present in a .csv file and we are going to analyse this data using Pandas Dataframe to answer a few questions

## Data Source : - Kaggle

## Project Outcomes:
#### By the time we finish this project we would have successfully answered a few questions:

### Query to Import our data 
```
cars_df = pd.read_csv('Cars Data.csv')
```
### Preview our Data
```
cars_df.head()
```
### A vivid description of our database
```
cars_df.describe()
```
### Number of unique columns in the database
```
cars_df.nunique()
```
### Unique Car Manufacturers in our Database
```
cars_df['Make'].unique()
```
### Finding and replacing null data in our database with the mean value of that column
```
cars_df.isnull().sum()
cars_df['Cylinders'].fillna(cars_df['Cylinders'].mean(),inplace=True)
cars_df.isnull().sum()
```
### Find the different Manufacturers in our database , and also find the count(occurence) of each make in the data
```
cars_df['Make'].value_counts()
```
### Show all records where Origin is Asia or Europe
```
cars_df[cars_df['Origin'].isin(['Asia','Europe'])]
```
### Remove all records(rows) where the weight is above 4000
```
cars_df.drop(cars_df[cars_df['Weight'] > 4000].index,inplace=True)
cars_df
```
### Increase the value of column 'MPG_City' by 4
```
cars_df['MPG_City'] = cars_df['MPG_City'].apply(lambda x : x+3)
cars_df.head()
```
## Visualisation

### visualise the number of different cars all manufactures had made
```
sns.countplot(x='Type',data=cars_df,lw=3,ec='black',hatch='/')
```
### Create a function to visualise the different no. of cylinders cars had on offer in our database
```
cars_df['No of Cylinders'] = cars_df['Cylinders'].apply(lambda x : "Equal to 6" if(x == 6) else "Less than 6" )
sns.countplot(x='No of Cylinders',data=cars_df,palette='Set1',lw=3,ec='black',hatch='/')
```
### Visualising the different weights of cars present on the basis of their origin
```
sns.displot(x='Weight',data=cars_df,hue='Origin',kind='kde')
```
### Ploting a relationship between 'EngineSize' and 'Horsepower'
```
sns.displot(y='EngineSize',x='Horsepower',data=cars_df,kind='kde',color='red')
```
### Plotting a EngineSize vs Mileage graph to find a relationship
```
sns.lmplot(x='EngineSize',y='MPG_City',data=cars_df,col='Origin',truncate=False)
```
### Mileage offered by the two widely made cars in our database in city as well as highway
```
sns.lmplot(x='MPG_Highway',y='MPG_City',data=cars_df[cars_df['Type'].isin(['Sedan','Sports'])],truncate=False)
```
### Mileage offered by different cars in city and on highway on the basis of their origin
```
sns.lmplot(x='MPG_Highway',y='MPG_City',data=cars_df,col='Origin', truncate=False)
```

## Project Setup:
To clone this repository you need to have Python compiler installed on your system alongside pandas and seaborn libraries. I would rather suggest that you download jupyter notebook if you've not already.

To access all of the files I recommend you fork this repo and then clone it locally. Instructions on how to do this can be found here: https://help.github.com/en/github/getting-started-with-github/fork-a-repo

The other option is to click the green "clone or download" button and then click "Download ZIP". You then should extract all of the files to the location you want to edit your code.

Installing Jupyter Notebook: https://jupyter.readthedocs.io/en/latest/install.html<br>
Installing Pandas library: https://pandas.pydata.org/pandas-docs/stable/install.html









