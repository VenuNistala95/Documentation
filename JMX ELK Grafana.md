# How to set up JMX, ELK, Grafana connection

**1. JMX**

Download apache JMeter 5.4.1. Open Apache Jmeter.jar from the bin folder after extracting the downloaded zip. 
Import the JITANA.jmx file available in this git repo. 
You might need to install elastic search plugin from plugin manager. 
Backend listener for elastic search is already configured in the JMX script. 

**2. Elastic Search**
Download elastic search from the website. Make sure to download the version 7.0.0 which is compatible with the grafana that we will set up later. 
extract the downloaded zip folder. Go to bin folder , open command prompt and run the command "elasticsearch.bat"
This will spin up elastic search on your localhost:9200. Open this port in the browser which will give a JSON formatted out put with the ELK version.

**3. Grafana**

Download Grafana version 7.0.0 from the official website.
On the left panel, click on the gear icon and select "Add data source" 
Search for "Elastic search"
In the configuration  provide URL : http://localhost:9200
index: test
datefield: Timestamp

Click on save and test. Datasource will be successfully update. 
You might get an error "No datefield Timestamp is found" This is a bug and can be ignored. 

Now go back to Grafana home page. Click on import dashboard and import by pasting the JSON content available in this git repo. File is named "JSONJMX.json"
This is the dashboard which will provide information from the elastic search.

Now run the JMX test on your local which will send data to elastic search and will reflect on the Grafana dashboards.
