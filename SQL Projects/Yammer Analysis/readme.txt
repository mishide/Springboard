Hola Mundo!


Python was used to analyze and recommend reasons for the recent drop in user engagement on the Yammer application.  


Data notes:  Since the SQL that raised concerns only reported on event_type of "engagement", analysis was performed on this subset only.  


Analyses:   looked at individual devices, devices grouped by device type, and top 75% companies using the application.  Initial results show majority of issues with phones and the #1 customer, company 1, being the only ones impacted. 


Data Files:  4 CSV files included in this repo:
* event.csv
* users.csv
* emails.csv
* rollup.csv


Note:  For comparison, SQL used in "SQL Yammer Analysis" is displayed, followed by python code to perform the same analysis.