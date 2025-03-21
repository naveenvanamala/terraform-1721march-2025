# Day 5

## Lab - Developing our own custom Terraform file provider in Golang
Make sure the below folder is created
```
mkdir -p /home/rps/go/bin
```

Create file name .terraformrc under your home directory /home/rps/.terraformrc with the below content
<pre>
provider_installation {
  dev_overrides {
      "registry.terraform.io/tektutor/file" = "/home/rps/go/bin",
  }
  direct {}
}  
</pre>

Now you may build your 
```
cd ~\terraform-1721march-2025
git pull
cd Day5/DevOpsCICDPipeline/custom-terraform-provider/file
tree
go mod init github.com/hashicorp/terraform-provider-file
go mod tidy
go build
go install
```

Expected output
![image](https://github.com/user-attachments/assets/564594be-5580-493f-9494-31cce3114ef5)
![image](https://github.com/user-attachments/assets/f54673af-4bee-4902-a507-25abdea6cc17)
![image](https://github.com/user-attachments/assets/97e393a0-fade-42de-8628-3293560a9742)
![image](https://github.com/user-attachments/assets/cf4395d1-c186-4e8b-9c24-b125352648f7)
![image](https://github.com/user-attachments/assets/a6e923ca-7817-4081-aa51-a6056514c866)

## Lab - Using our custom file provider in a terraform project
```
cd ~\terraform-1721march-2025
git pull
cd Day5/DevOpsCICDPipeline/test-terraform-provider-file-provider
ls -l
terraform plan
terraform apply --auto-approve
ls -l
```

Once you are done with this exercise, you may dispose the resources provisioned by Terraform
```
terraform destroy --auto-approve
ls -l
```

Expected output
![image](https://github.com/user-attachments/assets/9fb97d74-22e6-4aa1-a62f-9ace1c5182ca)
![image](https://github.com/user-attachments/assets/2a0d3791-ab59-4b0e-9f7f-3f90b8fcb977)
![image](https://github.com/user-attachments/assets/d55b6218-dab9-4ae9-83e7-d6079083fb61)
![image](https://github.com/user-attachments/assets/c0623ebd-d305-4b68-bf58-28e99dc975e9)
![image](https://github.com/user-attachments/assets/f606302a-3597-4032-8763-3fd0e8a32ba8)


## Lab - Developing a custom docker container terraform provider in golang
```
cd ~\terraform-1721march-2025
git pull
cd Day5/DevOpsCICDPipeline/custom-terraform-provider/docker
tree
go mod init github.com/hashicorp/terraform-provider-docker
go mod tidy
cat ~/.terraformrc
go build
go install
```

Expected output
![image](https://github.com/user-attachments/assets/f9eaaf77-5cde-4752-8764-25053b55645c)
![image](https://github.com/user-attachments/assets/ac72e6c8-1b49-4150-938c-4d8b52ec38bb)
![image](https://github.com/user-attachments/assets/f5825d99-4af4-4672-a42b-ab0ce30487d2)
![image](https://github.com/user-attachments/assets/5da0d887-1815-498d-910a-6f1b8bfc6c6b)


## Lab - Using our custom terraform docker provider plugin in Terraform Project
```
cd ~/terraform-1721march-2025
git pull
cd Day5/DevOpsCICDPipeline/test-terraform-provider-docker-provider
terraform plan
terraform apply --auto-approve
```

Expected output
![image](https://github.com/user-attachments/assets/2b1bd399-0ffb-411f-87b9-bd07e7a2575d)
![image](https://github.com/user-attachments/assets/38d8d55d-de04-4cbf-993d-5bce2e5eab16)
![image](https://github.com/user-attachments/assets/46b15d9f-7ebb-45f3-a24b-6ff4a80b7bf8)

Once you are done with this exercise, you may dispose the docker containers provisioned by terraform
```
terraform destroy --auto-approve
```
Expected output
![image](https://github.com/user-attachments/assets/f34a1074-bd9e-4ac4-a83d-a51a2b786bfe)

                                                                                                                                  
                                                                                                                                  
                                                                                                                                  
## Info - Infrastructure automation test cases ( Sentinel Policy Management )
https://developer.hashicorp.com/terraform/tutorials/policy/sentinel-policy

## Info - Terraform Module
<pre>
- is a collection of many terraform scripts(*.tf) files in a dedicated folder
- modules encpasulate group of terraform resources related to a single infrastructure/task
- modules allows us to resue code
- the terraform scripts kept in the top-level folder is reerred as root module
- the terraform scripts kept in the top-level sub-folder is referred as child module
- a root module may have zero to many child modules
</pre>

## Info - Terraform Module vs Terraform Provider
<pre>
- Terraform Provider is developed by a Terraform Provider developer using golang programming language
- Terraform Module is written by DevOps Engineers who use the Terraform provider
- Terraform Module is written in HCL(Hashicorp Configuration Language) will file extensions *.tf
- Terraform Module is written in declarative code
- Terraform Modules are reusable code that can be invoked from Terraform Root modules
- Terraform Modules can be reused across many Terraform Projects
- Terraform Modules depends on one or more Terraform Providers
- Terraform Projects is nothing but the top level folder that has the below
  - Terraform Providers
  - Terraform Root Module
    - Terrafoorm child Module(s) optionally
</pre>

## Lab - Developing a custom terraform module and invoking it from Terraform root module
```
cd ~/terraform-1721march-2025
git pull
cd Day5/terraform/modules
terraform init
terraform plan
terraform apply --auto-approve
terraform show
docker ps
```

Expected output
![image](https://github.com/user-attachments/assets/14431b97-7e6f-4fcc-a8b4-7385131263b0)
![image](https://github.com/user-attachments/assets/e90de3af-8163-48c2-b1de-4b6ff7552aa1)
![image](https://github.com/user-attachments/assets/ec32b05d-4e9d-4f38-b817-a85774f46fc3)
![image](https://github.com/user-attachments/assets/b785eebb-362b-4c93-8a62-715a91c1602a)
![image](https://github.com/user-attachments/assets/355d25b1-2315-4d29-8aeb-956f8b6e83bf)
![image](https://github.com/user-attachments/assets/0e6875fa-432d-46df-acda-fd075b2b552d)
![image](https://github.com/user-attachments/assets/a67f6bff-1a53-4dce-86af-f0d3674d1ecc)
![image](https://github.com/user-attachments/assets/cd6d0155-1a0b-412e-a05e-427ab9d24f1f)
![image](https://github.com/user-attachments/assets/ad03276e-ab96-4f1a-b9fd-c74fe60bf4dd)
![image](https://github.com/user-attachments/assets/1c62c1fb-3842-42f9-8c41-2cf127af45ce)
![image](https://github.com/user-attachments/assets/c7f9a58e-be27-4ac6-b87b-6a7df59c9a91)
![image](https://github.com/user-attachments/assets/b7fb6d28-3312-45f5-8df2-adc2e1a149df)
![image](https://github.com/user-attachments/assets/e626ce52-fc18-4d52-a615-c2a1071788ac)



## Info - Terraform Provider Development best practices and recommended naming conventions
<pre>
- Provider name must be terraform-provider-nameoftheprovider, must be all lower case
- Resource names must start with nameoftheprovider-resource i.e docker_container, docker is the provider name while the resource managed is container
- resource and data source name must be all lowercase separated by underscore, and recommened to restrict to 2 or 3 words at the max
</pre>

## Info - Commons causes of Configuration Drift
<pre>
- manual changes
- inconsistent and manual deployments
- external dependencies
- difference in environments
- lack of version control
- poor or lack of documentation
</pre>

## Info - Risks associated with Configuration Drifts
<pre>
- Security Vulnerabilities
- Performance issues
- Compliance issues
- Makes troubleshooting very difficult
- increased down-time
- decreased reliability
- poor user-experience
</pre>

## Info - Solution to Configuration Drifts
<pre>
- Using Version Control
- Continuous Integration
- Use Configuration Management Tools to override manual changes in continuous fashion
- Use Infrastructure as Code Tools to override manual changes
- Regularly monitor and audit infrastructure
</pre>

## Info - Monitoring
<pre>
- is the process of collecting and analyzing data from IT infrastructure, system and processes
- using the data to improve business outcomes and drive value to the organization
- collects data to help keep your infrastructure up and running without any downtime
- Tools to
  - Data Collection (Logs)
  - Alerting
  - Remediation
  - Agent based monitoring
  - Agentless monitoring
  - Collecting Metrics
- Examples
  - Dynatrace
  - DataDog
  - Splunk
  - Prometheus & Grafana
</pre>

## Continuous Integration (CI) Overview
<pre>
- it is a fail-fast engineering process to find issues early 
- when bugs are detected early during development phase, they are easy to fix
- cost of fixing the bugs is also relatively cheaper
- it is similar SCRUM daily stand-up meeting, which is an inspect and adapt meeting
- the team that follows CI/CD, the engineers would be pushing code to version control several times a day
- code would be integrated many times a day
- Jenkins or similar CI/CD server will grab the latest code, they trigger a build, as part of the build, automated test cases would be executed to verify if the new code is as expected, if the new code is breaking any existing functionality.
- the build that was triggered due to new code integration succeeds, it means no functionality is broken, everything works as expected
- continous frequent feedback is given by CI/CD builds, eventually improving the code quaility and functional quality
- CI helps confidently deliver releases in a short amount of time
- Unit and Integration is the scope of CI
</pre>

## Continuous Deployment (CD) Overview
<pre>
- Once the dev release suceeds all the automated test cases added by dev team, it is automatically promoted for QA testing
- the dev certified release binaries are deployed automatically to QA environment for further automated QA testing
- the QA would automate, end to end functionality test, regression test, smoke test, performance test, stress test, component/API test, etc
</pre>

## Continuous Delivery (CD) Overview
<pre>
- the QA certified build(release) is automatically deployed into production or pre-prod environment
- in the pre-prod environment the customer or the Operations team would verify if the new release is working as expected
- especially fintech companies, after manual approval the binaries could go live in production environment
</pre>

## What is Jenkins?
- is a build automation server
- used mainly for CI/CD Builds
- this was developed in Java by Kohsuke Kawaguchi, former employee of Sun Microsystems
- Initially it was developed as Hudson is an opensource project
- Then Oracle acquired Sun Microsystems, then part of Hudson including Kohsuke Kawaguchi had quit Oracle
  created a new branch from Hudson called Jenkins
- The other part of the Hudson team they continue to develop the product as Hudson
- There is lot common code between Hudson and Jenkins
- More than 10000 active contributors are there for Jenkins
- Many other software vendors got inspired by Jenkins similar products came out in market like Bamboo, Team City, Microsoft TFS, etc.,
- Jenkins supports CI/CD build for products built in any software stack
  
## What is Cloudbees?
- Cloudbees is the enterprise paid variant of Jenkins
- Feature wise Jenkins and Cloudbees pretty much they are same
- We get support for Cloudbees while we only get community support for Jenkins
- Cloudbees is more stable as it is a paid version
  
## Jenkins Alternatives
- Bamboo
- Team City
- Cloudbees ( Enterprise Jenkins )
- Microsoft Team Foundation Server (TFS)

## Lab - Download Jenkins war file
Download the Generic Java Package (war) file from the left side (LTS)
<pre>
cd ~/Downloads
wget https://get.jenkins.io/war-stable/2.492.1/jenkins.war
</pre>

Expected output

## Lab - Launching Jenkins from terminal
```
cd ~/Downloads
java -jar ./jenkins.war
```

Expected output
![image](https://github.com/user-attachments/assets/3020ac7f-4302-4a42-b835-cfc1a171428d)

## Lab - Accessing Jenkins Dashboard from your RPS Cloud machine chrome web browser
<pre>
http://localhost:8080  
</pre>

Expected output
![image](https://github.com/user-attachments/assets/c500acf9-8e35-4b6c-b758-6e21185f1016)
![image](https://github.com/user-attachments/assets/ca8d24b7-69e6-4d28-8a9d-134529cc64f9)
![image](https://github.com/user-attachments/assets/c70b66fc-eb7f-419b-9348-bcf131abcbd1)
![image](https://github.com/user-attachments/assets/dcabdd19-ec4a-43ed-88a4-94f98b1147ce)
Click "Continue"
![image](https://github.com/user-attachments/assets/333ce131-fd6f-4a55-b704-2b83ebf66df7)
Select "Install suggested plugins"
![image](https://github.com/user-attachments/assets/2ddd07b9-1b31-4b5a-8f85-2a50ba213dc2)
![image](https://github.com/user-attachments/assets/94a319c9-36f4-4faa-b0f6-e5702db636e5)
![image](https://github.com/user-attachments/assets/7b2858db-8ef1-4e78-88a8-a532840b11e3)
![image](https://github.com/user-attachments/assets/c13e183d-ed93-45d6-85cc-9a4b3327c6cd)
![image](https://github.com/user-attachments/assets/a8be3b00-6720-4e86-b7bc-d87e762c052d)
![image](https://github.com/user-attachments/assets/2b7f7661-c198-48a2-9c23-c8cc0ba4cc7b)
![image](https://github.com/user-attachments/assets/8f5d4b57-6ec7-41ae-88c6-adfefa54b547)
![image](https://github.com/user-attachments/assets/e68ad809-3535-41a5-8e04-46d5573bd3b5)
Click "Save and continue"
![image](https://github.com/user-attachments/assets/50806f3d-08fc-4921-830b-110bf7cf887c)
Click "Save and Finish"
![image](https://github.com/user-attachments/assets/3d618bd9-c889-41c7-ab8b-a00c85295bb2)
Click "Start using Jenkins"
![image](https://github.com/user-attachments/assets/f3a86e91-1b69-40e8-9c0b-a337ae087f1e)

## Lab - Creating a Jenkins Job
Navigate to your Jenkins Dashboard on the RPS Lab Web browser
![image](https://github.com/user-attachments/assets/7a8edad7-a3b8-4503-adec-e11f072a3a3c)

Click "Create Job"
![image](https://github.com/user-attachments/assets/5e1a31f0-bef6-4c33-b458-8358f107ac8a)

Select "Pipeline", type "DevOpsCICDPipeline" under "Enter an item name" 
![image](https://github.com/user-attachments/assets/fad0a2d6-eb7a-4044-aac4-aac44724b465)
Click "Ok"
![image](https://github.com/user-attachments/assets/ae71e9b0-7523-4c46-a28e-07842f88ef51)

General Section
![image](https://github.com/user-attachments/assets/b208a2e0-4ee6-493b-aaa6-7d7cab5af0d5)

Triggers Section
Select the checkbox "Poll SCM"
Under the Schedule type "H/02 * * * *" to configure Jenkins to poll GitHub every two minutes
![image](https://github.com/user-attachments/assets/c90abeab-af4f-479e-9517-e32a687a12a5)

Pipeline Section
![image](https://github.com/user-attachments/assets/0b5f7b1a-0c59-4469-a713-0ff840c30b77)
Under Definition, Select "Pipeline script from SCM"
![image](https://github.com/user-attachments/assets/165d0eb7-f86a-419e-b5de-1dc278fe3d0b)
![image](https://github.com/user-attachments/assets/9f8efaaf-ea77-4020-8473-cf919b2c70ef)
Under SCM, select "Git"
![image](https://github.com/user-attachments/assets/9d49439b-cef0-4d4e-af2b-63560b1ef8d4)
Under the Repository URL paste "https://github.com/tektutor/terraform-1721march-2025.git"
![image](https://github.com/user-attachments/assets/3386af0b-e50e-425d-a467-f319dc0fd1b5)
Under Branch specifier, replace master with main
![image](https://github.com/user-attachments/assets/5790ef08-afbf-4791-8ec4-30d2a1fad674)
Under the Script Path update Jenkinsfile to Day5/Jenkinsfile
![image](https://github.com/user-attachments/assets/59007a2f-c649-46f8-8116-ce0078e1229b)
Click "Save"
![image](https://github.com/user-attachments/assets/2dd1054e-3845-42b9-bdb6-87b7587719e0)

Progress
![image](https://github.com/user-attachments/assets/0261307b-e4fc-4cbc-9e48-e122c16ec855)

Failed
![image](https://github.com/user-attachments/assets/03b6828a-14ea-4d87-875f-dae9fa258521)

Success
![image](https://github.com/user-attachments/assets/f1460e4c-bbd6-4d45-a308-005059f12ccb)
![image](https://github.com/user-attachments/assets/18c961db-63d1-4f45-af90-2cf8dfdfbc83)
![image](https://github.com/user-attachments/assets/f573cc62-51b3-42be-a0c7-2a02cabf7f02)
![image](https://github.com/user-attachments/assets/89e42e47-f163-427f-9c22-8f0dc1d5918a)

