# Energy Track & Trace marginal impact analysis

Code for estimating Energy Track & Trace's marginal impact on power system dispatch.

This code is provided for transparency purposes.
Data files used in the analysis are not included in this repository.

## Required files

### data/portfolios.csv

Table assigning renewable energy sources to portfolios.

Columns:
* `id`: Unique ID of the portfolio.
* `site`: Unique ID of the site.

Example:
```
id,site
P1,S1_solar
P2,S2_solar
P2,S2_wind
```

### data/sites/{site}.csv

Energy production data for RES sites.
Folder folder must contain one CSV-file for each site specified in `portfolios.csv`.

Columns:
* `time`: Start time for production hour in UTC.
* `electricity`: Produced energy in kWh.

Example:
```
time,electricity
2019-01-01 00:00,2019-01-01 01:00,1115.831
2019-01-01 01:00,2019-01-01 02:00,245976.090
...
2019-12-31 22:00,2019-12-31 23:00,584432.432
2019-12-31 23:00,2020-01-01 00:00,216081.941
```

CSV files produced with [renewables.ninja](https://renewables.ninja) are compatible.

### data/price.csv

Energy spot prices in EUR for each hour.

Columns:
* `time`: Start time for hour.
* `price`: Spot price in EUR/kWh.

Example:
```
2019-01-01 00:00:00+01:00,0.02832
2019-01-01 01:00:00+01:00,0.01007
...
2019-12-31 22:00:00+01:00,0.03888
2019-12-31 23:00:00+01:00,0.03739
```

### data/co2.csv

CO2 emission factors in g/kWh for each hour.

Columns:
* `time`: Start time for hour.
* `co2`: CO2 emission factor in g/kWh.

Example:
```
2019-01-01 00:00:00+01:00,221
2019-01-01 01:00:00+01:00,195
...
2019-12-31 22:00:00+01:00,352
2019-12-31 23:00:00+01:00,364
```
