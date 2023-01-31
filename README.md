# Description

a 3-step project using `SQS`, `Lambda`, `CloudWatch`, `Postgres` and infrastructure as code : 
- a new file containing tabular data is uploaded by a user to an s3 bucket in a specific folder (`new_data/`)
- a cron will trigger a lambda that will move this file to another folder (`processing/`) so that an s3 event is generated
- event message is sent to a lambda using SQS to feed a postgres table

# What is involved ?
- `python` : the programming language that is used on the server side
- `terraform` : is an open-source infrastructure as code software tool that enables you to safely and predictably create, change, and improve the infrastructure of this project
- `LocalStack` : to run AWS applications or Lambdas entirely on a local machine without connecting to a remote cloud provider
- `Docker` : to packages code and its dependencies so the application runs quickly and reliably across computing environments
- `postgres` : an open source object-relational database system

# What do I need to use this repo ?

- `Docker`
- internet connection

# Quick start : 

- `make docker-compose` : builds image of the project and runs containers (wait until terraform container finishes its job)
- `make list-objects-in-bucket` : shows the content of your s3 bucket
- `make list-lambda-functions` : shows the list of your lambda functions
- `make list-sqs-queues` : shows the list of your SQS queues
- `make send-new-data-to-bucket index_file=1` : sends a csv file to s3 bucket, there are 2 files in the project, write `index_file=2` if you want to send the other dataset
- `make test-lambda function_name=trigger-processing-function` : invokes lambda `trigger-processing-function` which is in charge to move datasets from folder `new_data/` to folder `processing` which triggers an s3 event notification
- `make query-table-read` or `make query-table-count` to check if the table has been updated
