
# 07 - Docker Hub Integration with Azure Dev Pipelines

- Docker image how we can Dockerize the code repositories 

<img src="./../img/C_32.png" alter="Fundamental"/> 

### General 
- Let's say we have a Maven Project 
- After build we get a War file 
- That file Deploye any machine which is runing Tomact server for (Request, Response) of the project Live

### Docker Image 
- War file -> Deployee Tomcat -> Make docker Image  
- Find any machine and then start Docker container (Image)

### Docker Hub 
- is Open Platform where we can Upload/Download docker Images 
- Any one can Download and Run this Image in any machine 

<img src="./../img/C_33.png" alter="Fundamental"/> 

### Create New Pipeline 

- Select Docker this time 

<img src="./../img/C_34.png" alter="Fundamental"/> 

- Or Another Way 
- After Build It create Docker Image (YAML instruction)

<img src="./../img/C_35.png" alter="Fundamental"/> 
<img src="./../img/C_36.png" alter="Fundamental"/> 



