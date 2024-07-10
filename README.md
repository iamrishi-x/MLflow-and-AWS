# MLflow-and-Dagshub
This is basic understanding for implementation of MLflow and Dagshub remote server operation for comparison metrics

# ML Flow

![](https://img.shields.io/github/stars/pandao/editor.md.svg) 
![](https://img.shields.io/github/forks/pandao/editor.md.svg) 
![](https://img.shields.io/github/tag/pandao/editor.md.svg) 
![](https://img.shields.io/github/release/pandao/editor.md.svg) 

**Table of Contents**

## For Dagshub:

MLFLOW_TRACKING_URL=https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow/ \
MLFLOW_TRACKING_USERNAME=iamrishi-x \
MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef \
python script.py


```bash
export MLFLOW_TRACKING_URL=https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow/
export MLFLOW_TRACKING_USERNAME=iamrishi-x
export MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcefo
```
## Issues faced
###### Issue 1 - urllib3>=2.0 does not work with system Python on macOS 
Solution [Downgrade piplib3 version to < 2.0.0 ](https://stackoverflow.com/questions/76187256/importerror-urllib3-v2-0-only-supports-openssl-1-1-1-currently-the-ssl-modu "Heading link")

###### Issue 1 - Connection in use: ('127.0.0.1', 5000)
Solution Instead of https://127.0.0.1:5000/ url
http://localhost:5000/ worked for me in macos 
