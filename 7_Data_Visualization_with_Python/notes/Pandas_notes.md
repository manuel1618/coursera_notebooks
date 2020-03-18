# Pandas Notes

## Cleaning data

- clean up the dataset to remove unnecessary columns (eg. REG)

```python
df_can.drop(['AREA', 'REG', 'DEV', 'Type', 'Coverage'], axis=1, inplace=True)
```

- let's rename the columns so that they make sense

```python
df_can.rename(columns={'OdName':'Country', 'AreaName':'Continent','RegName':'Region'}, inplace=True)
```

- for sake of consistency, let's also make all column labels of type string

```python
df_can.columns = list(map(str, df_can.columns))
```

- set the country name as index - useful for quickly looking up countries using .loc method

```python
df_can.set_index('Country', inplace=True)
```

- add total column

```python
df_can['Total'] = df_can.sum(axis=1)
```

- years that we will be using in this lesson - useful for plotting later on

```python
years = list(map(str, range(1980, 2014)))
print('data dimensions:', df_can.shape)
```
