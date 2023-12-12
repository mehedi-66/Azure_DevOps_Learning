
# Creating Pipeline 

-  First Need to understand **Agents** 


<img src="./img/Pipeline_1.png" alter="Pipeline 1" />

- Pipeline means Series of Action/Task can be automated 
-  Test to Go Live this part can be automated (Test, build, publish, UAT server , Go Live (with Permition Email))

- Planing => Execution => Pipeline => Artifacts


<img src="./img/Pipeline_2.png" alter="Pipeline 2" />

### Defining and Understanding Agents in Azure DevOps
#
- To build, test we need machine, CPU 
- Agent is a software which run inside machine and executes the pipeline task.
- Agent execute the task serially 

### Using project settings to configure agents 


<img src="./img/Agent_1.png" alter="Agent 1" />

- Inside settings => Pipelines => Agetn Pools 



<img src="./img/Agent_2.png" alter="Agent 2" />

- Hosted Agent => gives by Azure Team
- Hosted Agents and Local agents (Self Hosted agents)

<img src="./img/Agent_3.png" alter="Agent 3" />



### Creating pipeline and Running the Pipeline 

- Create pipeline 
- Select the Project Repo 


<img src="./img/Create_Pipeline_1.png" alter="Create Pipeline 1" />

- Select the Project

<img src="./img/Create_Pipeline_2.png" alter="Create Pipeline 2" />

- Configure the Project Acordingly 

<img src="./img/Create_Pipeline_3.png" alter="Create Pipeline 3" />


- Review your pipeline YAML
- YAML is a Markup language 
- YAML file and versioning in Azure repos. 
- YAML file where your Pipeline Task are Written 

- Save and Run the YAML file 

<img src="./img/Create_Pipeline_4.png" alter="Create Pipeline 4" />


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

<img src="./img/Yaml_1.png" alter="yaml 1" />



- We want to run the job faild 
- Understanding the "No hosted parallelism Error" in Azure DevOps

<img src="./img/Yaml_2.png" alter="yaml 2" />


- We create our own **Agent**
- To solve Parallelism issue 
- Hosted Agent not Free now
- To create New Agent by Own 
- Agent Pools means => Pool of computer
- Add Pool


<img src="./img/CreatePool_1.png" alter="Pool 1" />

- Pool Type is Self Hosted (Local machine)

<img src="./img/CreatePool_2.png" alter="Pool 1" />



- Agent nothing but a software 
- A software by Download Agnet 

<img src="./img/AgentPC_1.png" alter="AgentPC 1" />


- Extract the download file 

- Configure the agent by 
- PS C:\agent> .\config.cmd



<img src="./img/cmd_1.png" alter="Cmd 1" />



<img src="./img/Cmd_2.png" alter="Cmd 2" />



<img src="./img/Cmd_3.png" alter="Cmd 3"/>

- PAT => Personal Access Token 




<img src="./img/Cmd_4.png" alter="Cmd 4"/>

- Gives pool name 


<img src="./img/Cmd_5.png" alter="Cmd 5" />

- Work folder where run, build, latest file 
- Enter with y 




- Optionally run the agent interactively 
- PS C:\agent> .\run.cmd
- Listien it out of job 

<img src="./img/Cmd_6.png" alter="Cmd 6"/>

### After Creating local Agent pool 
- Change the YAML file 
- So that YAML file indicate the (our own Agent Pool)



<img src="./img/Cmd_7.png" alter="Cmd 7"/>

- YAML Edit by  mycomputeragent




<img src="./img/Cmd_8.png" alter="Cmd 8"/>

- Running YAML pipeline with Self hosted agents 
- Step by Step task execute 



<img src="./img/Cmd_9.png" alter="Cmd 9"/>





