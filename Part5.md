1. Integration
The integration process involves importing the data from my MySQL database into Excel and ensuring that it is formatted correctly for analysis. 

I used the SQL command SELECT * INTO OUTFILE to export my database tables as CSV file.

Command:
SELECT * FROM MergedVaccinationData
INTO OUTFILE '/var/lib/mysql-files/MergedVaccinationData.csv'
FIELDS TERMINATED BY ',' ENCLOSED BY '"'
LINES TERMINATED BY '\n';

Open Excel and Import CSV File:
Open Microsoft Excel and go to the Data tab.
Click on Get External Data > From Text/CSV.
Browse to the location where you saved your exported CSV file and select it for import.
Ensure that the delimiter settings match the structure of your data (usually comma-separated).

Clean and Format Data:
Once the data is imported into Excel, verify the formatting.
Remove any unnecessary columns or rows if needed.
Check for any inconsistencies such as missing values or duplicates and clean the data accordingly.

Setup Pivot Tables and Charts:
Select the imported data and create pivot tables to structure the data for analysis.
Use the pivot tables as the source for charts that you will use in the dashboard.
Ensure that the field settings for the pivot table reflect the desired metrics.