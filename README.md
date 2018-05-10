# Python-Learning

# Dcitionaries
example_dictionary = {}

### Adding item to dictionary:
example_dictionary[item]=example_value

# Modules
### Imports modelue
import math (as m) >>> math.sqrt(10)
import csv >>> cvs.reader(data)
import numpy
import pandas

# Working with Classes
class Dataset:
    def __init__(self, data):
        self.header = data[0]
        self.data = data[1:]
    
    def __str__(self):
        string_data = self.data[:10]
        return str(string_data)
    
    def column(self, label):
        if label not in self.header:
            return None
        
        index = 0
        for idx, element in enumerate(self.header):
            if label == element:
                index = idx
        
        column = []
        for row in self.data:
            column.append(row[index])
        return column
    
        
    def count_unique(self, label):
        unique_results = set(self.column(label))
        count = len(unique_results)
        return count
    
nfl_dataset = Dataset(nfl_data)
print(nfl_dataset)
Dataset.column(nfl_dataset,'winner')

# Enumerate Function 
for i, item in enumerate(data) >>> gives index 'i' and element 'item' in 'data' list

# Try function 
for year in legislators:
    newyear=year[2]
    birth_year=newyear.split("-")[0]
   
    try:
        birth_year=int(birth_year)
    except Exception:
        birth_year = 0
    year.append(birth_year)

# Extracting last value 
last_value = 1 
for row in legislators:
    if row[7] == 0:
        row[7] = last_value
    last_value = row[7]

# List Comprehension 
sample = [row[5] for row in data] 

# Extracting Max Value 
max_value = None 
for name in name_counts:
    count=name_counts[name]
    if max_value is None or count>max_value:
        max_value=count
print(max_value)

# Items function 
race_per_hundredk = {}
for k,v in homicide_race_counts.items():
    race_per_hundredk[k] = (v / mapping[k]) * 100000   >>> 
>>> Creates Dictionary where one dic values are devided by other dic values. 

# Pandas
food_info = pandas.read_csv("food_info.csv") >>> Reads in file 
data.head(n) >>> first n rows
data.columns >>> column names 
data.shape >>> structure of data frame; [0] - rows , [1] - columns 
data.loc[1] >>> extracting rows by index, counting from 1 
data.iloc[1] >>> extracting rows by position, counting from 0 
data = data[column_name] >>> extracting columns 

### Normalizing values
food_info >>> Dataframe
normalized_protein=
(food_info["Protein_(g)"] - food_info["Protein_(g)"].min())/
(food_info["Protein_(g)"].max() - food_info["Protein_(g)"].min())
x(normalized)=(x-x(min))/(x(max)-x(min))

### Adding new column
food_info["Normalized_Protein"]=normalized_protein, where
normalized_protein >>> dataframe column filled with values 

### Adding New Column
food_info["name"]=dataframe

### Sorting Values 
food_info.sort_values("Norm_Nutr_Index", inplace=True, ascending=False)>>>
>>> inplace >>> means that we sort in the same Dataframe. 

### Is null
is_null = pandas.isnull(dataframe)

### Populate empty values with mean 

Type1
age_is_null = pd.isnull(titanic_survival["age"])
good_ages=titanic_survival["age"][age_is_null == False]
correct_mean_age = sum(good_ages)/len(good_ages)

Type2
correct_mean_age = titanic_survival["age"].mean() >>> automatically excludes missing values when calculating mean 

### Calculating Fare Mean for Each Passenger Class

Type1:
passenger_classes = [1, 2, 3]
fares_by_class = {}
for psngcl in passenger_classes:
    pclass_rows = titanic_survival[titanic_survival["pclass"] == psngcl]
    pclass_fares=pclass_rows["fare"]
    fare_for_class=pclass_fares.mean()
    fares_by_class[psngcl] = fare_for_class
    
Type2:
passenger_age=titanic_survival.pivot_table(index="pclass", values="age",aggfunc=np.mean), 
where index>>> column to group by 
      values>>> value column to perfrom operation
      aggfunc>>> what operation to perform on values 
      
### Dropping rows or columns from matrix
new_titanic_survival = titanic_survival.dropna(axis=0, subset=["age","sex"]), where axis = 0 >> row , axis = 1 >>> column

### Selecting particular rows/columns
row_index_1100_age =new_titanic_survival.loc[1100,"age"]
row_index_25_survived= new_titanic_survival.loc[25,"survived"]
five_rows_three_cols= new_titanic_survival.iloc[:5,:3]  >>> first 5 rows, first 3 columns. 

### Reindexing Dataframe after sorting 
titanic_reindexed = new_titanic_survival.reset_index(drop=True)

### Finding total jobs for each unique major 
aa_cat_counts = dict()
rg_cat_counts = dict()

def count_totals(dataframe):
    categories=dataframe["Major_category"].unique()
    counts_dictionary=dict()
    
    for category in categories:
        data_major = dataframe[dataframe["Major_category"] == category]
        total = data_major["Total"].sum()
        counts_dictionary[category] = total 
    return counts_dictionary

aa_cat_counts = count_totals(all_ages)
rg_cat_counts = count_totals(recent_grads)

### Count Wages according to Major in two different sets 

All majors, common to both DataFrames
majors = recent_grads['Major'].unique()
rg_lower_count = 0

for major in majors: 
    recent_grads_row=recent_grads[recent_grads["Major"] == major]
    all_ages_row=all_ages[all_ages["Major"] == major]
    
    rg_unemp_rate=recent_grads_row.iloc[0]["Unemployment_rate"]
    aa_unemp_rate=all_ages_row.iloc[0]["Unemployment_rate"]
    if rg_unemp_rate < aa_unemp_rate:
        rg_lower_count = rg_lower_count+1
        
print(rg_lower_count)

### Creating series 
Type1 : 
film_names = series_film.values
rt_scores = series_rt.values

series_custom = Series(rt_scores, index=film_names)
print(series_custom)

Type2: 
movies=fandango[["FILM","RottenTomatoes"]], where fandango is dataframe

### Sorting indexes and values in series object
sc2=series_custom.sort_index()
sc3=series_custom.sort_values()


# Working with Dataframes

### creating new sub-dataframe based on some index 
fandango_films = fandango.set_index("FILM", drop=False, inplace=False)

### Using apply and lambda function to calculate across rows(0) or columns(1)

Rows:
import numpy as np
types = fandango_films.dtypes
float_columns = types[types.values == 'float64'].index
float_df = fandango_films[float_columns]
deviations = float_df.apply(lambda x: np.std(x))

Columns:
rt_mt_user = float_df[['RT_user_norm', 'Metacritic_user_nom']]
rt_mt_means = rt_mt_user.apply(lambda x: np.mean(x), axis=1)

### Values counts function.  pd.data.value_counts 

# Data Cleaning 
### Reading multiple files into a dictionary

import pandas as pd
data_files = [
    "ap_2010.csv",
    "class_size.csv",
    "demographics.csv",
    "graduation.csv",
    "hs_directory.csv",
    "sat_results.csv"
]
data = {}
for f in data_files:
    d=pd.read_csv("schools/{0}".format(f))
    key_name=f.replace(".csv", "")
    data[key_name]=d
    
### Combining two dataframes
survey=pd.concat([all_survey, d75_survey], axis=0), where axis=0 >>> putting one frame  below the other

### Copying columns
data[new_column]=data[old_column]
