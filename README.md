# example of project deployed locally

a 3-step project using `SQS`, `SNS`, `Lambda`, `CloudWatch`, `Postgres` and infrastructure as code : 
- a new file containing tabular data is uploaded to an s3 bucket in a specific folder
- a cron will trigger a lambda that will move this file to another folder so that an s3 event is generated
- event message is sent to a lambda using SQS to feed a postgres table

# dependencies
- `python` : the programming language that is used on the server side
- `terraform` : is an open-source infrastructure as code software tool that enables you to safely and predictably create, change, and improve the infrastructure of this project
- `LocalStack` : to run AWS applications or Lambdas entirely on a local machine without connecting to a remote cloud provider
- `Docker` : to packages code and its dependencies so the application runs quickly and reliably across computing environments
- `aws-cli` : a command line interface to interact with `AWS` objects
