# IDS706-miniProject 12
Duke IDS 706 Data Engineering Project: working with MLflow Project
Updating from https://github.com/nogibjj/python-template
Followed tutorial from https://www.coursera.org/learn/mlops-mlflow-huggingface-duke/lecture/KKsD1/create-an-mlflow-project



## Create an MLFlow Project

For this project, we'll use a small CSV file with data about wines, called [wine-ratings.csv](wine-ratings.csv).

### Step 1: Start with the dependencies

1. setting up a Conda environment first. Even if you prefer using `pip` for installing dependencies, you can still define that with a Conda environment.

```
conda create --name exploratory python=3.8
```

2. activate the environment so that packages are installed in that activated environment.

```
conda activate exploratory
```

3. Next, with the _exploratory_ environment activated export the dependencies so a new YAML file named _conda_env.yml_

```
conda env export --name exploratory > conda_env.yml
```


Append a few lines to use `pip` to install `mlflow`, `pandas`, `click` which is used in python CSV validation.

```yaml
  - pip:
    - mlflow
    - pandas==1.5.0
    - mlflow==1.29.0
    - click==8.1.3

```

Run the following command to ensure everything is working and installed.

```
 conda env update --file conda_env.yml --prune
```

### Step 2: Run the MLproject with validate.py

1. First run the project with an example CSV file which contains validation errors. This example will provide warnings as shown below.

```
mlflow run . -P filename=carriage.csv
```

Command Result:
![carriage.csv result](<img/mlflow_success.png>)


2. After testing its functionality, we can work with a valid CSV file.

```
mlflow run . -P filename=wine-ratings.csv
```

CommandResult: 
![wine.csv result](<img/ml_wine.png>)


