## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

```
# Step 1: Import Necessary Libraries

import pandas as pd
import numpy as np
from sklearn.preprocessing import LabelEncoder, StandardScaler, PowerTransformer
from scipy.stats import boxcox

# Step 2: Load the Dataset

import pandas as pd

data = pd.read_csv("Data_to_Transform.csv")

print("Original Dataset:")
print(data.head())
```
Original Dataset:
   Moderate Positive Skew  Highly Positive Skew  Moderate Negative Skew  \
0                0.899990              2.895074               11.180748   
1                1.113554              2.962385               10.842938   
2                1.156830              2.966378               10.817934   
3                1.264131              3.000324               10.764570   
4                1.323914              3.012109               10.753117   

   Highly Negative Skew  
0              9.027485  
1              9.009762  
2              9.006134  
3              9.000125  
4              8.981296

```
#Handle Missing Values (Fill numeric columns with mean)

data.fillna(data.mean(numeric_only=True), inplace=True)

```

# RESULT:
       # INCLUDE YOUR RESULT HERE

       
