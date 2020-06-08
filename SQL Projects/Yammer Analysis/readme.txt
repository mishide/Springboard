Hola Mundo!


Python was used to analyze and recommend reasons for the recent drop in user engagement on the Yammer application.  The original report ran from a SQL query that used an event_type of "engagement".  Analyses  looked at individual devices, devices grouped by device type, top 75% companies using the application.


This analysis uses the 4 CSV files included in this repo:
* event.csv
* users.csv
* emails.csv
* rollup.csv


For comparison, some of the SQL used for analysis in file "SQL Yammer Analysis" is displayed, followed by the python used to perform the same analysis.