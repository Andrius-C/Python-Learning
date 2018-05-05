# Python-Learning

# Dcitionaries
example_dictionary = {}

### Adding item to dictionary:
example_dictionary[item]=example_value

# Modules
### Imports modelue
import math (as m) >>> math.sqrt(10)
import csv >>> cvs.reader(data)

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
