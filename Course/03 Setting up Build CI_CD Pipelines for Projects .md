# Setting up Build CI_CD Pipelines for Projects  

- different Pipeline are Azure Pipelines

<img src="./../img/C_5.png" alter="Fundamental"/>

- Create Pipeline 

<img src="./../img/C_6.png" alter="Fundamental"/>

- Select Repository 

<img src="./../img/C_7.png" alter="Fundamental"/>

- Configure you Pipeline 

<img src="./../img/C_8.png" alter="Fundamental"/>

- Review you YAML file 
- **Pool** means a machine where it has CPU, Ram, memory so that it can build the project 

<img src="./../img/C_9.png" alter="Fundamental"/>

- Run the project 


<img src="./../img/C_9.png" alter="Fundamental"/>

<img src="./../img/C_10.png" alter="Fundamental"/>

# 

- To Get of the build project war copy to s1 to a folder of _work direactory  

<img src="./../img/C_11.png" alter="Fundamental"/>

- To Added into  Pipeline 

<img src="./../img/C_12.png" alter="Fundamental"/>

- To Add this Artifact into Build publish 

<img src="./../img/C_13.png" alter="Fundamental"/>
<img src="./../img/C_14.png" alter="Fundamental"/>

- After run the YAML file we get Artifacts

<img src="./../img/C_15.png" alter="Fundamental"/>

- Publish build Artifacts War file place into Unique #Id


<img src="./../img/C_16.png" alter="Fundamental"/>

# 
### CI => Continous Integratoin Happening How
- When you push code into master branch 
- Autometicaly build Pipeline Triger 
- You have to Mention What is the condition for Trigger 

<img src="./../img/C_18.png" alter="Fundamental"/>
<img src="./../img/C_17.png" alter="Fundamental"/>



