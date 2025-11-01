# Automation pipeline: AzurePipeline.RDS.Shutdown
This repository features an Azure Pipeline designed to automate the process of shut down an RDS instance in AWS. Includes a command to shut down RDS. This configuration optimizes infrastructure management, reduces manual work, and ensures that instances are properly shut down.

### 🛠️For the use the schema
* Aws account and a RDS
* Azure devOps account
* * Create new pipeline
* * Add variables in the pipeline

#### Pipelines variables
```
AWS_ACCOUNT_ACCESS_KEY_ID
AWS_ACCOUNT_SECRET_ACCESS_KEY
AWS_INSTANCE_ID
AWS_REGION
```

### ⚡Triggers in Azure Devops
We can configure pipelines to run on the days we need:
- Create pipeline in Azure Devops
- Setting pipeline with this repository and azure-pipelines.yml
- Select Triggers and Scheduled
- Scheduled detail:

<div align="center">
  <img height="300" width="90%" src="triggers.png"  />
</div>