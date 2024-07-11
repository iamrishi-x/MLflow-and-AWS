# MLflow-and-Dagshub
This is basic understanding for implementation of MLflow and Dagshub remote server operation for comparison metrics

## URLs
```shell
Dogshub url="https://dagshub.com/iamrishi-x/MLflow-and-Dagshub"
Github url="https://github.com/iamrishi-x/MLflow-and-Dagshub"
Experemental Dogshub url="https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D"
local url="http://localhost:5000/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D"
```

# ML Flow

![](https://img.shields.io/github/stars/pandao/editor.md.svg) 
![](https://img.shields.io/github/forks/pandao/editor.md.svg) 
![](https://img.shields.io/github/tag/pandao/editor.md.svg) 
![](https://img.shields.io/github/release/pandao/editor.md.svg) 

**Table of Contents**

## For Dagshub Cred Configuration:
### Method 1
```bash
export MLFLOW_TRACKING_URL=https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow/
export MLFLOW_TRACKING_USERNAME=iamrishi-x
export MLFLOW_TRACKING_PASSWORD=27810455efc1b096f0e2ae6609d29ec0e1557aae
```
```python
url="https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow"
```
---
### Method 2
#### 1. Initialize DagsHub Repository:
```python
import dagshub
dagshub.init(repo_owner='iamrishi-x', repo_name='MLflow-and-Dagshub', mlflow=True)
```

#### 2. Log Parameters and Metrics with MLflow:

```python
import mlflow
with mlflow.start_run():
    mlflow.log_param('parameter name', 'value')
    mlflow.log_metric('metric name', 1)
```
#### 3. Environment Variables :
```sh
export DAGSHUB_USER='<your_username>'
export DAGSHUB_PASSWORD='<your_password>'
```
#### 4. Credentials File:
Create a .netrc file in your home directory with the following content:

```sh
machine dagshub.com
login <your_username>
password <your_password>
```
#### 5. Run Your Script:
Execute your Python script to start logging to DagsHub via MLflow.

## Issues faced
###### Issue 1 - urllib3>=2.0 does not work with system Python on macOS 
Solution [Downgrade piplib3 version to < 2.0.0 ](https://stackoverflow.com/questions/76187256/importerror-urllib3-v2-0-only-supports-openssl-1-1-1-currently-the-ssl-modu "Heading link")

###### Issue 1 - Connection in use: ('127.0.0.1', 5000)
Solution Instead of https://127.0.0.1:5000/ url
http://localhost:5000/ worked for me in macos 
