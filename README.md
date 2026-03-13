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
<img width="819" height="380" alt="image" src="https://github.com/user-attachments/assets/46e0c575-63ae-483d-8690-8a751039f029" />

```
#Handle Missing Values (Fill numeric columns with mean)

data.fillna(data.mean(numeric_only=True), inplace=True)

```

<img width="1006" height="478" alt="image" src="https://github.com/user-attachments/assets/9dfb7287-b4dc-4f10-a1d0-597ab8f98291" />

```

#Select a suitable numeric column for transformation

numeric_column = data.select_dtypes(include=np.number).columns[0]

print(f"\nColumn Selected for Transformation: {numeric_column}")

```

Column Selected for Transformation: Moderate Positive Skew

```

#Keep only positive values for log and boxcox

positive_data = data[data[numeric_column] > 0].copy()

#Log Transformation

positive_data['Log_Transform'] = np.log(positive_data[numeric_column])

#Reciprocal Transformation

positive_data['Reciprocal_Transform'] = 1 / positive_data[numeric_column]

#Square root Transformation

positive_data['Sqrt_Transform'] = np.sqrt(positive_data[numeric_column])

#Square Transform

positive_data['Square_Transform'] = np.square(positive_data[numeric_column])

#Box_cox Transform

positive_data['BoxCox_Transform'], lambda_value = boxcox(positive_data[numeric_column])

print(f"\nBox-Cox Lambda Value: {lambda_value}")

#Power Transform

pt = PowerTransformer(method='yeo-johnson')
data['YeoJohnson_Transform'] = pt.fit_transform(data[[numeric_column]])

#StandardScaler

scaler = StandardScaler()
data['Standard_Scaled'] = scaler.fit_transform(data[[numeric_column]])

```

```

#StandardScaler

scaler = StandardScaler()
data['Standard_Scaled'] = scaler.fit_transform(data[[numeric_column]])

```
<img width="873" height="598" alt="image" src="https://github.com/user-attachments/assets/b06b2701-6822-4ddf-845e-e7a54cc33e6b" />


# RESULT:
 Thus the Implementation of Feature Encoding and Feature Transformation executed successfully.

       
