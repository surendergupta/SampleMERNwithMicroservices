# SampleMERNwithMicroservices

## Git fork and clone

1. Project Link: https://github.com/UnpredictablePrashant/SampleMERNwithMicroservices
2. Fork this repository. For the update from the main repository, you can follow these steps:
```
mkdir SampleMERNwithMicroservices
cd SampleMERNwithMicroservices
git init
git remote add upstream https://github.com/UnpredictablePrashant/SampleMERNwithMicroservices.git
git fetch upstream
git checkout main
git merge upstream/main main
git rebase upstream/main 

```

## Project Steps:
1. Set Up the AWS Environment

Download AWS CLI below link as per your OS:

```
[ ASW CLI ](https://aws.amazon.com/cli/)

```

Afers Installation check AWS version:

```
aws --version

```

Output:

```
aws-cli/2.15.36 Python/3.11.8 Windows/10 exe/AMD64 prompt/off

```

Now Configure your AWS:

```
aws configure 
AWS Access Key ID : <ACCESS_KEY> 
AWS Secret Access Key: <ACCESS_SECRET_KEY> 
Default region name [us-east-1]: us-east-1
Default output format [json]: json

```

Now AWS CLI configure Successfully

Move to BOTO 3

In Windows you craete virtual envinorment on Linux Skip this.

```
python -m venv venv
venv\Scripts\activate

```

Install Boto 3

```
pip install boto3

```

To verify AWS CLI and BOTO 3 configure correctly create test.py file and put below code :

```
import boto3

# Create an S3 client
s3 = boto3.client('s3')

# List all S3 buckets
response = s3.list_buckets()

# Print bucket names
print('S3 Buckets:')
for bucket in response['Buckets']:
    print(f'  {bucket["Name"]}')

```

To execute the test.py file

```
python .\test.py

```

Output:

```
S3 Buckets:
  b3devlambda
  codepipeline-us-east-2-783934304898
  daniel-boto3-2
  daniel-boto3-29
  daniel-boto3-3
  daniel-boto3-4
  daniel-boto3-5
  darwinbox

```

If you getting the S3 list from your AWS Account is show AWS CLI and BOTO 3 configure correctly.


2. Prepare the MERN Application

Containerize the MERN Application:

Create a Dockerfile for each component (frontend and backend).

Dockerfile of frontend

```
FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

```

Image Build of front

```

docker build -t simple_mern_micro_fe .

```

Dockerfile of frontend
