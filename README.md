# React Chart using data from Liferay Objects (7.4)
Example of populating data into a React Chart ([FusionCharts](https://www.fusioncharts.com/)) from a API that was created through Liferay Objects (7.4).

### Expected Use
This resource can be used as a 7.4 Remote App (iFrame or Custom Element) or a separate React App altogether.

## Install Packages
Once downloaded run:

yarn install

## Start local server
yarn start

## Create Dashboard Data Object

1. Create Object named:

    * Label: "Dashboard Data Object"
    * Pural Label: "Dashboard Data Objects"
    * Name: "DashboardDataObject"

2. Object Needs the Fields

    | Field  |  Type     | Required  |
    | :---   |   :----:  |  :----:   |
    | Label  | String    | Yes        |
    | Value  | Integer   | Yes       |

3. Leave the object configuration in Company Scope

4. Return to the Details tab and publish your new object.

## Add Data

1. Using the newly created API enpoint for dashboarddataobjects, find the bulk endpoint

    Example: http://localhost:8080/o/api/?endpoint=http://localhost:8080/o/c/dashboarddataobjects/openapi.json

2. Add the following data and press execute. This will add the number of records shown below.

```
[
    {
      "label": "Venezuela",
      "value": "290"
    },
    {
      "label": "Saudi",
      "value": "260"
    },
    {
      "label": "Canada",
      "value": "180"
    },
    {
      "label": "Iran",
      "value": "140"
    },
    {
      "label": "Russia",
      "value": "115"
    },
    {
      "label": "UAE",
      "value": "100"
    },
    {
      "label": "US",
      "value": "30"
    },
    {
      "label": "China",
      "value": "30"
    }
  ]
  ```
  
## Use as separate React App
  
1. Using 'yarn start' start the server. It should hit Liferay's headless API using Basic Authentication (test@liferay.com:test over port 8080)
 
2. Once the server is running, you should be able to see the application running on it's own server at http://localhost:3000/ or similar. 
 
## Remote App (iFrame) 
  
1. Once the server is running (se previous step), you should be able to see the application running on it's own server at http://localhost:3000/ or similar. 
    
2. Then, navigate to Remote Apps within Liferay's control panel.
    
3. Create a new Remote App with the following field details:

| Field    |  Value                  |
| :---     |         :----:          |
| Name     | React Bar Chart         |
| Type     | iFrame                  |
| URL      | http://localhost:3000/  |
    
Save, then this application will be available in your widgets list.
  
## Remote App (Custom Element)
  
1. Within your React App, run a build using 'yarn run build'
    
2. The resulting files will be seen within your react project within a folder named /build/
  
3. Note the files packages in the build log, they should appear similar to this:
    
```
File sizes after gzip:

509.77 KB (-133 B)  build/static/js/2.f86fd244.chunk.js
1.39 KB (+1 B)      build/static/js/main.c7b9ace8.chunk.js
787 B               build/static/js/runtime-main.1ad6e658.js
132 B               build/static/css/main.26c647c1.chunk.css
```

4. Place the build folder within your Liferay webapps/ folder and rename the build folder react-bar-chart/ or similar.

5. Then, navigate to Remote Apps within Liferay's control panel.
    
6. Create a new Remote App with the following field details. 
    * *Note: Reference the build names from the previous step.*
    * *Note: Use the (+) icon for adding additional URL values.* 

| Field    |  Value                                                                   |
| :---     | :---                                                                     |
| Name     | React Bar Chart                                                          |
| Type     | Custom Element                                                           |
| URL 1    | http://localhost:8080/react-bar-chart/static/js/2.f86fd244.chunk.js      |
| URL 2(+) | http://localhost:8080/react-bar-chart/static/js/main.c7b9ace8.chunk.js   |
| URL 3(+) | http://localhost:8080/react-bar-chart/static/js/runtime-main.1ad6e658.js |
| CSS      | http://localhost:8080/react-bar-chart/static/css/main.26c647c1.chunk.css |
    
Save, then this application will be available in your widgets list.
