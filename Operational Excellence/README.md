#### Achieving Operational Excellence
```
Does not require automating everything
Define your workflows and AWS resources as code
Code is repeatable and executes quickly
Easily track changes 
```
#### Cloud Formation => AWS iaas
```
AWS developer Tools: Code Commit is same as git on AWS
Code Deploy
Code Pipeline
```
#### AWS Systems Manager
```
OS Patching
Cloud Watch Events, Auto Scaling lifecycle hooks and AWS Config
```
#### IAM Principals and Policies
```
Configuring the AWS CLI
Cloudformation terminiology
```
#### Lab Setup

#### Stacks

> [TIP]
> AWS resources that you create, update and delete as a single unit.

#### Template

Code is stored in tempale
JSON or YAML documents that describe AWS resources.

#### Divided into sections

- Parameters
- Mappings
- Resporces(required)
- Outputs

Cloudformation must read template from s3.

#### Multiple Stacks

Different teams manages different resources
Resources have different lifecycle.
Distributing resources across different stacks makes tthem easier to  manage.

#### Module Overview
```
Stack Policies
Stack output and exports
Nested Stacks
Helper Scripts
```

> [!TIP]
> Get Export Value

#### Outputs
```
PublicSubnets1:
  Description: Public subnet 1 ID
  Value: !Ref PublicSubnet1
  Export:
  Name:
    !Sub "${AWS::StackName}-PublicSubnet1"
```
