# EDA (Exploratory Data Analysis) with Pandas

## Database info

Exploratory analysis is of the telecom segment. The company has three sets of customer and service data, with a variable that determines whether the customer has endorsed (churn) or not the telecom company..

The purpose is that with these data sets and based on some hypotheses that we will formulate and that will be answered by the EDA, can obtain some initial insights for the construction of artificial intelligence that can "predict" the abandonment of still active customers.

- churn_customers.csv = Client data

- churn_contracts.csv = Contracts data

- churn_services.csv = Services data

## Collection of data

### Creating a dataframe by csv - read_csv

```python
df_contracts = pd.read_csv('./datasets/churn_customers.csv')
```

#### The firsts registers - head(x)

```python
df_contracts.head(5)
```

#### The last registers - tail(x)

```python
df_contracts.tail(5)
```

#### Dataframe info - info()

```python
df_contracts.info()
```

## Data transformation

#### Change column data type

```python
df_contracts.TotalCharges = pd.to_numeric(df_contracts.TotalCharges, errors='coerce')
```

#### Change column name

```python
# Rename some columns
df_customers.rename(columns={'SeniorCitizen': 'Above65YearsOld'}, inplace=True)
```

```python
# Rename using list - All columns
df_customers.columns = ['ClientID', 'Gender', 'Above65YearsOld', 'HavePartner', 'HaveDependents']
```

### Merging dataframes

```python
# Merging customers and services
df_temp = df_customers.merge(df_services, on=['ClientID'])
```

```python
# Merging customers and services - using diferents columns name to merge
df_churn_temp = df_temp.merge(df_contracts, left_on=['ClientID'], right_on=['customerID'])
```

### Removing columns

```python
df_churn.drop(['customerID'], axis=1, inplace=True)
```

### Missing values detection

```python
df_churn.isna().sum()
```

### Dealing with missing values

#### Drop

```python
# Remove the column with missing value
df_churn.drop(columns=['TotalCharges'], axis=1)
```

```python
# Remove columns with missing values
df_churn.dropna(axis=1)
```

```python
# Remove columns where ALL values are missing
df_churn.dropna(axis=1, how='all')
```

#### Input

```python
# Fill all values of the dataframe with 0
df_churn.fillna(0)
```

```python
# Fill default values depending on
df_churn.fillna(value={'TotalCharges': 0, 'Gender': 'Not declared'})
```

## Univariate Analysis

Univariate analysis is a fundamental statistical technique in the field of Artificial Intelligence (AI), used to examine and understand the behavior of a single variable in a dataset. In other words, it focuses on the analysis of one feature or variable at a time, without considering relationships with other variables.

### Hypotheses

1. Client age group has a strong association with Churn
2. A client who com less than 6 months of active contract is more prone to Churn
3. Customer with monthly contracts are prone to Churn
