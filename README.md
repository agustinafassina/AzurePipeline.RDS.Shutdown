# Automation pipeline: AzurePipeline.RDS.Shutdown
This repository features an Azure Pipeline designed to automate the process of shut down an RDS instance in AWS. Includes a command to shut down RDS. This configuration optimizes infrastructure management, reduces manual work, and ensures that instances are properly shut down.

### 🛠️For the use the schema
* Aws account and a RDS
* Azure devOps account
* * Install the [AWS Toolkit for Azure DevOps](https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.aws-vsts-tools) extension
* * Create an AWS service connection
* * Create new pipeline
* * Set the variables in azure-pipelines.yml

#### AWS service connection
The pipeline uses the `AWSShellScript@1` task, which authenticates through an Azure DevOps service connection instead of access keys stored in variables.

- Go to **Project Settings → Service connections → New service connection → AWS**
- Enter the Access Key ID and Secret Access Key (or a Role ARN to assume)
- Name it `aws-dev-connection` (or update `awsCredentials` in azure-pipelines.yml to match)

#### Pipeline variables
Defined directly in azure-pipelines.yml:

```yaml
variables:
  AWS_REGION: 'us-east-1'
  AWS_INSTANCE_ID: 'database-1,database-2'
```

Replace them with your actual region and RDS DB instance identifiers. `AWS_INSTANCE_ID` accepts one identifier or several separated by commas; the pipeline stops them one by one, since `aws rds stop-db-instance` takes a single identifier per call.

> Note: AWS automatically starts a stopped RDS instance again after 7 days.

### ⚡Triggers in Azure Devops
We can configure pipelines to run on the days we need:
- Create pipeline in Azure Devops
- Setting pipeline with this repository and azure-pipelines.yml
- Select Triggers and Scheduled
- Scheduled detail:

<div align="center">
  <img height="300" width="90%" src="triggers.png"  />
</div>

### 🔄 Workflow
Pipeline workflow overview:

<div align="center">
  <img height="300" width="90%" src="workflow.png"  />
</div>
