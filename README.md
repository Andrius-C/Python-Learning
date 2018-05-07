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
data.loc[1] >>> extracting rows 
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

