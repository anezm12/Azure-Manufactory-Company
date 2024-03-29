# Azure-Manufactory-Company

![mrj](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/3ff07e8b-eea3-4328-91b3-04d3a862bab4)


In this situation, it was required to elaborate a connection between structured data from SQL Server to Azure ecosystem in order to perform transformation and the injection of a cured data for further analysis. With this scenario in mind, the tools implemented to complete this task were Storage Account to store three containers each with a different level of transfromation. Azure Data Factory for building and monitoring the pipeline responsible for the move of only the wanted raw data from all the tables available into the data lake gen2 and for the integration with the two following services . Azure Databricks where two levels of transformation were done, in this particular case the tables modified were stored in different folders in one container. The first transformation was to modify the date format from column ‘ModifiedDate’  with the objective to have a clearer and more standard date format. Second, it was required to transform all the formatting types of all column names from all tables, to go from ThisExample to This_Example. Last step of loading the data, in Synapse Analytics with its component of integrate and develop, a second pipeline was built for taking the validated data and making it available in the warehouse. 


## Azure Data Factory

![datafactory pipeline](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/ea7069ce-29bc-437c-b94f-3b46daba138c)

This pipeline counts with four activities including one 'Copy data' activity inside of the 'ForEach'. The connection between SQL Server and Azure Data Factory was made through self-hosted integration runtime. Each activity was connected by a success arrow. To select only the sales tables the lookup activity had a query inside the settings (SQL query available in SQL queries folder).  


## Azure Databricks

For databricks, I used credential passthrough that allows you to authenticate automatically to Azure Data Lake Storage from Azure Databricks clusters using the identity that you use to log in to Azure Databricks. I created three notebooks. One for all mouting with each container needed. A second one to perform the first level of transformation, which consists of transforming the date type from "YYYY-MM-DD HH:mm:ss.SSS." to a simpler one “YYYY-MM-DD”. The second one, it was needed to transform all column titles from all tables, ‘ThisIsAnExample’ to ‘This_Is_An_Example’. 

Compute setting:

Summary
1 Driver
14 GB Memory, 4 Cores
Runtime
13.3.x-scala2.12
Standard_DS3_v2
0.75 DBU/h

----- Check the notebooks in Databricks folder -----


## Azure Synapse Analytics

![azure-synapse-pipeline](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/ea6194ff-480b-4ace-872f-d16d18d82965)

![synapse-pipeline-runconsumption](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/d713d6e0-746b-4d85-89fc-1b6769e7dda7)

In the final stage of the project, I utilized Azure Synapse Analytics for the loading process. With Azure Synapse Analytics featuring its own pipeline builder component, I leveraged it to extract metadata and executed a stored procedure within a ForEach activity. This activity is linked to the script run in the development section. Once the pipeline was up and running, all the views were loaded into the workspace and are now ready to be utilized.

----- Check the T-Sql script in SQL folder -----


## Conclusion 

All these services can perform the same activities. This project was implemented using all services to demonstrate the ability and adaptability to work with different tools in the Azure ecosystem. In the initial project flow diagram, Power BI was depicted as the final step. However, this specific task was not executed this time. I recommend that anyone interested in running this project should handle the data analyst duties.

