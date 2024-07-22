# Data Preparation & Data Cleaning

### 1. Importing Required Libraries

```python
import pandas as pd
```
---
### 2. Loading Dataset:

```python
df = pd.read_csv("Spotify Quarterly.csv")
print(df.info())
```
<img width="473" alt="image" src="https://github.com/user-attachments/assets/89655797-25a8-4878-9c21-a2138c2bcf21">

We have a total of 26 rows and 17 columns but the last row is **NULL** for all the columns except `Date` and `Premium ARPU`.

---
### 3. Checking for NULL values:

```python
print(df.isna().sum())
```

<img width="276" alt="image" src="https://github.com/user-attachments/assets/1d881292-f8a1-4011-ae5c-ff50643b0f48">

As stated in the **Data Card** of the database, this last row of data should be ignored and not consider for the analysis. Therefore we will get rid of the last row:

```python
pd.options.display.width = 0
df = df[0:len(df)-1]
print(df.info())
```
<img width="473" alt="image" src="https://github.com/user-attachments/assets/d1b1bafd-8b21-4424-b4ff-ff0b9ee871c5">

Now we have a total of 25 rows and 17 columns. All columns have 25 entries.

---
### 4. Checking for Duplicates:

```python
print(f'There are {df.duplicated().sum()} duplicates.')
```
<img width="284" alt="image" src="https://github.com/user-attachments/assets/5b24cc90-b260-4c55-b422-8d92784c276a">

---
Let's take a look at the first 10 rows of the database:

```python
pd.options.display.width = 0
print(df.head(10))
```

<img width="1337" alt="image" src="https://github.com/user-attachments/assets/6f3248e1-a488-44d0-b479-982da2e9a265">

---
### 5. Data Formatting:

Check data types:

```python
print(df.dtypes)
```

<img width="325" alt="image" src="https://github.com/user-attachments/assets/745fa72c-2203-4ff7-b9bf-f67a526e8f2d">

All columns have proper data types except `date` which is `object` data type. This needs to be changed:

```python
df['Date'] = df['Date'].astype('datetime64[ns]')
print(df.dtypes)
```

<img width="376" alt="image" src="https://github.com/user-attachments/assets/7cd45c3e-73bf-4dcb-981f-473d15255108">

