
# Definition and Understand Acronym of YAML

- Complete Azure Pipelie written by YAML 

- YAML => Yet Other Markup Language 
- YAML => Ain't Markup Language 

### some words 
- Its not like HTML
- Its not meant for documents.
- Its not meant for look and feel.
- Its not meant for positioning 

- YAML is a data serialization format for storing **configuration information**

<img src="./img/1_YAML.png" alter="yaml 1" />

#
## YAML basic name / value, space, indented, Nested objects & Hyphens 


- Practice YAML to json comverter 
https://onlineyamltools.com/convert-yaml-to-json

- Yaml Name: value 

<img src="./img/2_YAML.png" alter="yaml 2" />

- Space Indentation **not Tab** is important See Example 

<img src="./img/3_YAML.png" alter="yaml 3" />

- Hyphane **-** Represent the collection 

<img src="./img/4_YAML.png" alter="yaml 4" />

- Nested Object 

<img src="./img/5_YAML.png" alter="yaml 5" />

- Azure Generated code of YAML Understand 

<img src="./img/6_YAML.png" alter="yaml 6" />

- When some Push code into master This YAML Triger 
- pool Machine In our case mycomputeragetn
- It as some variables
- Step of **task** it should perform (Install NuGet => NwGetCommand => Build => Test)

<img src="./img/7_YAML.png" alter="yaml 7" />

- How to Assign Task Into YAML 
- The task Azure Team assign 
- We Set Into YAML file This way : 

<img src="./img/8_YAML.png" alter="yaml 8" />