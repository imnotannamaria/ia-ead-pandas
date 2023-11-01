# EDA (Exploratory Data Analysis) with Pandas

## Database info

Exploratory analysis is of the telecom segment. The company has three sets of customer and service data, with a variable that determines whether the customer has endorsed (churn) or not the telecom company..

The purpose is that with these data sets and based on some hypotheses that we will formulate and that will be answered by the EDA, can obtain some initial insights for the construction of artificial intelligence that can "predict" the abandonment of still active customers.

- churn_customers.csv = Client data

- churn_contracts.csv = Contracts data

- churn_services.csv = Services data

## Creating a dataframe by csv - read_csv

```bash
df_customers = pd.read_csv('./datasets/churn_customers.csv')
```

#### The firsts registers - head(x)

```bash
df_contracts.head(5)
```

#### The last registers - tail(x)

```bash
df_contracts.tail(5)
```

#### Dataframe info - info()

```bash
df_customers.info()
```
