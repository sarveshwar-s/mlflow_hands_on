# MLflow hands-on

In this repository, we will do a hands-on on:

- Tracking ML experiments with [MLflow tracking](https://www.mlflow.org/docs/latest/tracking.html)
- ML model management with [MLflow Model Registry](https://www.mlflow.org/docs/latest/model-registry.html)

We will use the [Cycle Power Plant dataset](https://archive.ics.uci.edu/ml/datasets/combined+cycle+power+plant)
in the different practical works, it is already in the `data` folder.

## Dataset

### Dataset description

The dataset contains 9568 data points collected from a Combined Cycle Power Plant over 6 years (2006-2011).
To goal is **to predict the net hourly electrical energy output (EP) of the plant**.

Features consist of hourly average ambient variables:

- **T**: Temperature
- **AP**: Ambient Pressure
- **RH**: Relative Humidity
- **V**: Exhaust Vacuum
- **EP**: Net hourly electrical energy output

The averages are taken from various sensors located around the plant that record the ambient variables every second.

### Dataset preparation

The dataset in the `data` folder is a concatenation of all the data in the raw excel file.
This was done with the following code:

```python
# install the version 1.2.0 of xlrd (pip install xlrd==1.2.0)

import pandas as pd

df_raw = pd.read_excel('/excel/file/path.xlsx', sheet_name=None)
df = pd.concat(df_raw, ignore_index=True)
df.to_csv("data/power_plants.csv", index=False)
```