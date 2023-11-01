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
