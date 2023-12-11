
# Creating Pipeline 

-  First Need to understand **Agents** 

![Pipeline 1](https://drive.google.com/uc?id=18VMovcEwWiU6VaW8RCMv-bMLF_3MkfUY)

- Pipeline means Series of Action/Task can be automated 
-  Test to Go Live this part can be automated (Test, build, publish, UAT server , Go Live (with Permition Email))

- Planing => Execution => Pipeline => Artifacts


![Pipeline 2](https://drive.google.com/uc?id=1-LkdrSojFciT9UGKws9e-CXvNLW9bVzv)

### Defining and Understanding Agents in Azure DevOps
#
- To build, test we need machine, CPU 
- Agent is a software which run inside machine and executes the pipeline task.
- Agent execute the task serially 

### Using project settings to configure agents 

![Agent 1](https://drive.google.com/uc?id=1ljF3RSdGxBDckjbdwGkj8X5xbL5kjQqp)

- Inside settings => Pipelines => Agetn Pools 

![Agent 2](https://drive.google.com/uc?id=1y16NhLNaotS5xu5K7HDkt8TEf3tGqMDh)

- Hosted Agent => gives by Azure Team
- Hosted Agents and Local agents (Self Hosted agents)

![Agent 3](https://drive.google.com/uc?id=1De-qJco8drGX2wmO3uSNx-zYXfZXawV9)


### Creating pipeline and Running the Pipeline 

- Create pipeline 
- Select the Project Repo 



![Create Pipeline 1](https://drive.google.com/uc?id=1bA2Cy2fS7qj4lOzReJs4-NxOt5N8rS5d)

- Select the Project


![Create Pipeline 2](https://drive.google.com/uc?id=1efK2kaXVeKYhaRA4CUYUDkV3whgptGuV)

- Configure the Project Acordingly 


![Create Pipeline 3](https://drive.google.com/uc?id=1940-Y9O5UgwH55dLv6QKWosiFmBYRaBX)

- Review your pipeline YAML
- YAML is a Markup language 
- YAML file and versioning in Azure repos. 
- YAML file where your Pipeline Task are Written 

- Save and Run the YAML file 


![Create Pipeline 4](https://drive.google.com/uc?id=1XN5xyPQeWppFM2BzZr_xQYidaYxkgNPx)


```yaml
# ASP.NET Core (.NET Framework)
# Build and test ASP.NET Core projects targeting the full .NET Framework.
# Add steps that publish symbols, save build artifacts, and more:
# https://docs.microsoft.com/azure/devops/pipelines/languages/dotnet-core

trigger:
- master

pool:
  vmImage: 'windows-latest'

variables:
  solution: '**/*.sln'
  buildPlatform: 'Any CPU'
  buildConfiguration: 'Release'

steps:
- task: NuGetToolInstaller@1

- task: NuGetCommand@2
  inputs:
    restoreSolution: '$(solution)'

- task: VSBuild@1
  inputs:
    solution: '$(solution)'
    msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:DesktopBuildPackageLocation="$(build.artifactStagingDirectory)\WebApp.zip" /p:DeployIisAppPath="Default Web Site"'
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: VSTest@2
  inputs:
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

```

- After save it commited to Repor 


![yaml 1](https://drive.google.com/uc?id=1N9CaH-v4o0irx9tqwC0U1vXfwMhrucLE)

- We want to run the job faild 
- Understanding the "No hosted parallelism Error" in Azure DevOps

![yaml 2](https://drive.google.com/uc?id=1-uX1HQhGh1Hb0cOyYIGRP0zKtte2cU66)

- We create our own **Agent**
- To solve Parallelism issue 
- Hosted Agent not Free now
- To create New Agent by Own 
- Agent Pools means => Pool of computer
- Add Pool



![Pool 1](https://drive.google.com/uc?id=1AQ2xZBKuhITFhRvGtscPe2mbz25IdnVY)

- Pool Type is Self Hosted (Local machine)

![Pool 2](https://drive.google.com/uc?id=1f5VZuYlCJivyAAF7IsBhqY88JIvPQww2)

- Agent nothing but a software 
- A software by Download Agnet 

![AgentPC 1](https://drive.google.com/uc?id=1GI6hWz_VSx336Nr1w4z9vl88teno3HoI)

- Extract the download file 

- Configure the agent by 
- PS C:\agent> .\config.cmd



![CMD 1](https://drive.google.com/uc?id=14PblotDUqBL4h1t3CGg4sRl4-LcO2sqg)




![CMD 2](https://drive.google.com/uc?id=1Qf6w1Uad2C5I11f7IcN8TePCjbWWR5OK)



![CMD 3](https://drive.google.com/uc?id=1EX-Y8guqPQyDGdsqRpbYGCiZK6crnBf-)

- PAT => Personal Access Token 




![CMD 4](https://drive.google.com/uc?id=1KgBS0w6XCJ7vPMBkm4XaHwlazcUkVlIo)

- Gives pool name 


![CMD 5](https://drive.google.com/uc?id=1csPRaBMn3yG0vcykqqIcsyeWuSr1dWQ8)

- Work folder where run, build, latest file 
- Enter with y 




- Optionally run the agent interactively 
- PS C:\agent> .\run.cmd
- Listien it out of job 


![CMD 6](https://drive.google.com/uc?id=1L-L9yALDkLvAk3tp834-71GS0XXfMKE4)

### After Creating local Agent pool 
- Change the YAML file 
- So that YAML file indicate the (our own Agent Pool)



![CMD 7](https://drive.google.com/uc?id=1R4nGm7FMAYXdUfmB1r2-jnesVzcc5t9A)

- YAML Edit by  mycomputeragent




![CMD 8](https://drive.google.com/uc?id=1UHk1TGg_tWVGsbGF5b-CtQkXjWWJDiSb)

- Running YAML pipeline with Self hosted agents 
- Step by Step task execute 




![CMD 9](https://drive.google.com/uc?id=1SpJKTEp4IcSDGWeY7dvT4BVgGdJ9ae_q)




