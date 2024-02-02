# Azure-Manufactory-Company

![mrj](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/3ff07e8b-eea3-4328-91b3-04d3a862bab4)


In this situation, it was required to elaborate a connection between structured data from SQL Server to Azure ecosystem in order to perform transformation and the injection of a cured data for further analysis. With this scenario in mind, the tools implemented to complete this task were Azure Data Factory for building and monitoring the pipeline responsible for the move of the raw data into the data lake gen2 and for the integration with the two following services . Azure Databricks where two levels of transformation were done, in this particular case the tables modified were stored in different folders in one container. The first transformation was to modify the date format from column ‘ModifiedDate’  with the objective to have a clearer and more standard date format. Second, it was required to transform all the formatting types of all column names from all tables, to go from ThisExample to This_Example. Last step of loading the data, in Synapse Analytics with its component of integrate and develop, a second pipeline was built for taking the validated data and making it available in the warehouse. 


## Azure Data Factory

![datafactory pipeline](https://github.com/anezm12/Azure-Manufactory-Company/assets/101163640/ea7069ce-29bc-437c-b94f-3b46daba138c)

This pipeline counts with four activities including one 'Copy data' activity inside of the 'ForEach'. The connection between SQL Server and Azure Data Factory was made through self-hosted integration runtime. Each activity was connected by a success arrow. To select only the sales tables the lookup activity had a query inside the settings (SQL query available in SQL queries folder).  
