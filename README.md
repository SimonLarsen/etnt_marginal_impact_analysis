# Energy Track & Trace marginal impact analysis

Code for estimating Energy Track & Trace's marginal impact on power system dispatch.

This code is provided for transparency purposes.
Data files used in the analysis are not included in this repository.

## Running

Add the required data files as specified under [Required files](#required-files) then run the notebooks `01_Analysis.ipynb` to compute the results and `02_Plot.ipynb` to generate the plots.

## Required files

### data/portfolios.yml

YAML file describing portfolios. Must be a list of records containing the following fields:

* `name`: Unique name of the portfolio.
* `area`: Name of area to fetch CO2 emissions and prices for.
* `sites`: List of RES sites in portfolio.

Example:
```yaml
- name: P1
  area: DK1
  sites:
    - S1_solar
    - S2_solar
- name: P2
  area: DK2
  sites:
    - S2_solar
```

### data/sites/{site}.csv

Energy production data for RES sites.
Folder must contain one CSV-file for each site specified in `portfolios.yml`.

Columns:
* `time`: Start time for production hour in UTC.
* `electricity`: Produced energy in kWh.

Example:
```csv
time,electricity
2019-01-01 00:00,2019-01-01 01:00,1115.831
2019-01-01 01:00,2019-01-01 02:00,245976.090
...
2019-12-31 22:00,2019-12-31 23:00,584432.432
2019-12-31 23:00,2020-01-01 00:00,216081.941
```

CSV files produced with [renewables.ninja](https://renewables.ninja) are compatible.

### data/price/{area}.csv

Energy spot prices in EUR for each hour in a specific area.
Folder must contain one CSV-file for each area specified in `portfolios.yml`.

Columns:
* `time`: Start time for hour.
* `price`: Spot price in EUR/kWh.

Example:
```csv
2019-01-01 00:00:00+01:00,0.02832
2019-01-01 01:00:00+01:00,0.01007
...
2019-12-31 22:00:00+01:00,0.03888
2019-12-31 23:00:00+01:00,0.03739
```

### data/co2/{area}.csv

CO2 emission factors in g/kWh for each hour for a specific area.
Folder must contain one CSV-file for each area specified in `portfolios.yml`.

Columns:
* `time`: Start time for hour.
* `co2`: CO2 emission factor in g/kWh.

Example:
```csv
2019-01-01 00:00:00+01:00,221
2019-01-01 01:00:00+01:00,195
...
2019-12-31 22:00:00+01:00,352
2019-12-31 23:00:00+01:00,364
```
