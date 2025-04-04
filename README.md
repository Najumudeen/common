## Core Concepts:
```
Origin
Observability
Golden Signals
SLIs, SLOs, Error Budgets
```
## Platform Overview
```
GCE
GKE
Cloud Run
Logging
Monitoring
```
### Fundamental Skills
```
Linux
Ip subnetting
Vi
CLI
Gcloud
Kubectl
Automation - bash, Python
```

### Deploy Demo Apps in GCP
```
GCE
GKE
Cloud Run
```

### Implement Observability
```
Glodne Signals
GCP Native
Grafana
```

### Project Creation

GCP Free Tier
Account ansd Initial Setup

Billing Export

Service Account Key => JWT token

### Cloud shell setup

gcloud configuration

### Site Reliability Engineer

Google Definition
Characteristics of a good SRE
Foundation Skill Set

Fundamentally, it's what happens when you ask a software engineer to design an opreations function.

Keys to SRE

# Google SRE Book

sre.google
sre-book

The most important feature of any system is its Reliability

### Golden Signals
```
Latency        # Response Time
Traffic        # Traffic, Is all the request your app is serving.
Error          # The app unable to handle the requiest and hence throws 5xx error
Saturation     # Metrics like Memory, cpu utilization and really reflect the health of your infrasture. Thses metrics are used
```
App is unable token

### Service Level Indicator(SLI)

A quantifiable measure of service Reliability.<br/>
Creafully choosen Monitoring metrics<br/>
Close relation between you user experience<br/>

```
SLI = (     good events )
     (     ----------- )          X     100%
     (      valid events)
```

Alerting Logics

Ignoring 3xx,4xx Error

### Service Level Objectives(SLO)

Set a Reliability target for an SLI

99.99

Latency SLIs is set for 200 ms

target SLO is 99% 

1 % request beyond 200 ms is OK, beyond that point then you are not achiving SLI.

Now we need to check 1 % request is Error Budgets

### Error Budgets

An SLO implies an acceptable level of unreliability This is a budget that can be allocated

### Availabilty Calculations


|  SLI Menu           |                                                 |
|    :--------        |   :--------                                     |
| Request / Response  |  Availabilty,  Latency,  Quality                |
|  Data Proeessing    |  Coverage,   Correctness, Freshness, Throughput | 
|  Data Proeessing    |  Throughput, Latency                            |


### Characteristics of a good SRE?
```
1. SRE Metrics => Can tell whether their app is healthy or unhealty in minutes
2. Believes in Extremm Automation - Saya no to doing the same thing manually more than twice.
3. Can define implement SLIs, SLOs, Error Budgets
4. Identify and build Reliability Fixes backlog for Dev teams
5. Looks for failure scenarios and thinks failovers. Example Third party apps failovers
6. Thiks Continous Improvement / Optimization
7. Love Logs 
```

### Fundamental Skill for SRE?
```
1. Know atleasrt 1 Public Cloud well
2. Understands Devops -Iac, CICD
3. Hands-on Git i.e. Code Versioning
4. Linux Know how - OS Distributions, Pacakge Managers, Essential commands, IP  address and subnets, vi editor
5. Master CLI - bash, linux, gcloud, kubectl
6. Understands basic networking, IP addr and CICR ranges
7. Automation - Bash/Powershell and/or Python
8. Knows Monitoring/Visualization Tools - Grafana, Dynatrace, Splunk etc
```

Birds Eye View


### Platform
```
GCP
AWS
AZURE
```

### GCP Cheetsheet click [here](https://googlecloudcheatsheet.withgoogle.com)


| GCP              | AWS                                      | Azure                                         |
| :----            | :-----                                   | :------                                       |
| GCE              | EC2                                      | Azure Virtal Machines                         |
| GKE              | EKS/ECS                                  | AKS                                           |
| Cloud Run        | Aws App Runner / AWS Fargate/ AWS lambda | Azure Container Apps/Azure Container Instance |
| Cloud Logging    | Amazon CloudWatch Logs                   | Azure Monitor Logs                            |
| Cloud Monitoring | Amazon Cloudwatch                        | Azure Monitor                                 |

* Adding Alias

    $HOME/.zshrc

    export 
    alias sre="cd $SRE"

------------------------------------------

### Microservices with Databases 

Anti Pattern Databases<br/>
Payment Service and User Service application talking to shared Database.<br/>
Issues, Dead Lock in DBMS<br/>
    
Use sepatae Database for each Microservices.
```
1. Scale service sepataely
2. Scale DB sepataely
```

### How to deal with distributed transaction?

Atomic that means ACID 

1. 2-Phase Commit

2. Saga Pattern => Message Broker 
                   Order service 
                   Event Driver Pattern
3. API Composition

Order Service application use 2 database.
1 read data from DB and write data from DB == CQRS
    
how to make data consistancy?

4. Event Sourcing system

 Create User
 Update User

 Event Logs => Kafka Stream<br/>
 Save data to kafka stream.<br/>
 triggers in MYSQL<br/>
 save all the snapshot or store the data.<br/>


### Build Large Scaling Microservices application
```
1. VPC
2. Services(App Layer)
3. User API, Products API, Order API
4. Each Service has own DB
5. Web Server(Nginx), Responsibel for LB, SSL certification, Ceritifcate Sits on LB
6. Async Falut Tollences use Messgae Broker(Kafka), Benfiti is grante delivery
7. Promethes /metrics endpoints for each service. Services reponsible publish metirs endpoint and Promethes scrap for there.
8. Grafana use Promethes as data source
9. Grafana notify to Slack channels notify us 
10. User Interface
11. BFF Server
```

### Coding Was Hard until I learned These 5 Things
```
1. Learning with doing
2. Learn to program not the programming language
3. Create a Roadmap
4. Priortize to Understands
5. Get used to failing
```
### Getcmd

> [!Note]
>  Search command from multiple *.md files 
```
getcmd -s "gcloud"
getcmd -s "kubectl custom colums"
```

### Getroles

> [!Note]
> Find the roles to kubernetes iam service. getroles monitoring.dashboards.create monitoring

### gcloud CLI Format
```
gcloud + release level (optional) + component + entity + operation + positional args + flags
```
For Example:
```
gcloud + compute + instance + create + example-instance-1 + --zone=us-central-a 
````
### output
```
gcloud compute instances list --format 'csv(NAME)'
gcloud compute instances list --format 'csv(NAME,ZONE)'
gcloud compute instances describe sreterminal
gcloud compute instances list --filter="NAME:$vm"
gcloud compute instances list --filter="NAME:$vm" --format json
gcloud compute instances list --filter="NAME:$vm" --format yaml
gcloud compute instances list --format="table[box](name,status)"
```
### Filter and sort result
```
gcloud compute machine-types list
gcloud compute machine-types list | wc 
gcloud compute machine-types list --filter="ZONE:us-east1-b"

Now narrow down to furter Search

gcloud compute machine-types describe c3d-highcpu-360 --zone us-east1-b 
gcloud compute machine-types list --filter="ZONE:us-east1-b AND name ~ highcpu"
gcloud compute machine-types list --filter="ZONE:us-east1-b AND name ~ highcpu AND name ~ n1"
gcloud compute machine-types list --filter="ZONE:us-east1-b AND name ~ highcpu AND name ~ n1" --sort-by CPUS,MEMORY_GB
```
### API Gateway vs Load Balancer vs Reverse Proxy

### Reverse Proxy (Nginx) / Reverse (Ingress) Proxy
```
1. Rate Limit
2. Authentication
3. IP filtering
4, Caching
5. SSL
6. Load Balancing
```

> [!TIP]
> LB is a subset of Nginx

### API Gateway
```
1. Reverser Proxy
2. Service Discovery
3. Circuit Breaking
```









 


