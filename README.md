# MLflow-and-AWS
This is basic understanding for implementation of MLflow and AWS remote server operation for comparison metrics

## URLs
```shell
Github url="https://github.com/iamrishi-x/MLflow-and-Dagshub"
AWS MLFLOW tracking url="http://ec2-43-204-234-14.ap-south-1.compute.amazonaws.com:5000/"
Experemental Dogshub url="https://dagshub.com/iamrishi-x/MLflow-and-Dagshub.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D"
local url="http://localhost:5000/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D"
```

# #ML Flow
## Workflows

1. Update config.yaml
2. Update secrets.yaml [Optional]
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline 
8. Update the main.py
9. Update the dvc.yaml

- [Documentation](https://mlflow.org/docs/latest/index.html)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
![](https://img.shields.io/github/tag/pandao/editor.md.svg) 
![](https://img.shields.io/github/release/pandao/editor.md.svg) 

---

### MLflow on AWS Setup:
1. Login to AWS console.
2. Create IAM user with AdministratorAccess - [ mlflow-user ]
3. Export the credentials in your AWS CLI by running "aws configure"
4. Create a s3 bucket [ mlflow-buckettt ]
5. Create EC2 machine (Ubuntu) & add Security groups 5000 port [ mlflow-aws-machine ]

```shell
sudo apt update
sudo apt install python3-pip
sudo pip3 install pipenv
sudo pip3 install virtualenv
mkdir mlflow
cd mlflow
pipenv install mlflow 
pipenv install awscli 
pipenv install boto3 
pipenv shell

/-- above not worked for me it showed errors --/
sudo apt update
sudo apt install python3-pip
mkdir mlflow
cd mlflow
sudo apt install python3-venv
python3 -m venv .venv
source .venv/bin/activate
pip3 install mlflow
pip3 install awscli
pip3 install boto3
pip3 install setuptools
## Then set aws credentials
aws configure

#Finally 
mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-buckettt

#open Public IPv4 DNS to the port 5000

#set uri in your local terminal and in your code 
export MLFLOW_TRACKING_URI="http://ec2-43-204-234-14.ap-south-1.compute.amazonaws.com:5000/"

```
---
## AWS exit
1. Terminated EC2 instance 
2. Deleted data from S3 bucket
3. Delete IAM user 
To avoid AWS charge

## Issues faced
###### Issue 1 - Error in AWS Ec2 instance
Solution [creating venv in AWS ](https://askubuntu.com/questions/1465218/pip-error-on-ubuntu-externally-managed-environment-%C3%97-this-environment-is-extern "Heading link")
```python
*Create a virtual environment using venv or virtualenv

*Make sure venv is installed by running:
sudo apt install python3-venv

*To create a new virtual environment in a directory named .venv, run:
python3 -m venv .venv

*To activate this virtual environment (which modifies the PATH environment variable), run this:
source .venv/bin/activate
```