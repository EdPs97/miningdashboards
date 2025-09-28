# miningdashboards
I spent year and a half in the Operational Excellence Department. One of my responsabilities was to create tools that allows the operational director and the Operational Excellence Team monitor the production compliance. The challenge was to summarize the whole operation in a few clicks, i.e. to transition from static tables to a friendlier graphical and dynamic interface. To obtain the following result it was necessary to understand the data sources from our company and how to request them in an automatically reliable fashion. The work presented here involved multidepartment interaction and a comprehensive knowledge of the company data flow. The creation of this Dashboards required mostly DAX, Power M and SQL knowledge whereas the maintenance also demand some basic Power BI gateway knowledge. 

Context and challenges 
A common practice among managers was to look for daily production in a local web site called SIREP that includes our targets in terms of tonnage, flow, grades and some consumption ratios. The format of this platform is a table that contains the actual value and its comparison to forecast and budget targets. Data is shown daily, monthly, quarterly and yearly. This means that they can filter by date, however only one day can be selected. Thus analysis between two different quarters is not allowed. Futher analysis required by managers is conducted by their subordinates that download data from SIREP or uses the information available On-Premise or in their SCADA systems. It has to be mentioned that SIREP data is the source of information that the corporation uses and publishes because it is regarded as the oficial values, which grants it the upmost relevance. The IT is responsible for the correct funtioning of SIREP, however, I was in charge of the data that was being reported to SIREP. 


*Image of SIREP 


An improved approach 
The dashboard was conceived as a dynamical source of data the present the same data as SIREP (our oficial data source) that updates daily and does To-Date calculations, moving average vs actual vs tagets graphs, calculations of the adjusted production to meet targets, and projections based of our latest performance and trend indicators. The idea was to create multiple reports so that users can click on graphs or values to go for the details. The top-down approach was possible using Power BI features. 

*Images that illustrate the granularity of the dashboard 


In terms of the data source I query the data available in the SIREP SQL database. This worked for both the actual and target values (budget and forecast), except for weighted averages which required some extra steps. For this variables it was necessary to pivoted the tables and add columns in Power Query. 

*Image of PowerQuery 

As mentioned before the idea was to publish this Dashboard within our organization. For this matter I created a Work Space in Power BI and add all the users that will be interested in looking at this data. In order to set the automatical updates I requested to IT a Server where I can install a Gateway instead of running the Gateway on-premise. Then I schedule two updates per day at 11:30 and 12:00. 

*Image of the Gateway and the Workspace. 



Final result 
The dashboard allows users to navigate through Mine, Crushing and the Processing Plant and mining equipment mechanical availability values. The main page can be filtered by month or quarter and sums up data in three columns: To-Date compliance, trend and production adjustments to meet targets (except for ounces which shows the amount of ounces left to extract in the given period). The trend is represented by a triangle and an equal sign; the logic behind is straightforward: the triangle will point upwards and will be green if the last actual value is 5% greater than its predecessor and will be painted red point downwards anytime where the value is less than 5% than its predecessor. The equal sign will appear if the new value remaains within that -+5%. 

This gives you a insight on the overall performance, however if the user is interested in the values depicted for a certain variable they can click on it and the report will take them to another page that contains detailed information. 


*Image of the main page 


Each variable has its own report that depicts the following: a line plot with the actual value, the moving average (7 days) and the target, the cummulative compliance encircled by colored ring, the last moving average value, the moving average projection supposing the last moving average value mantains through the rest of the month/quarter, the final target value in the month or quarter, the projected compliance in percentage and the production adjustment which refer to the value that should be achieved daily so that we can reach the monthly/quarterly goal. 


*Image of both reports 



Comments 
With this implementation directors and managers can have a quick view of the production performance, how far or close we are to our targets and what would it take to meet our goals. The simplicity works because it can help to answer the most recurrent questions in an executive circle. The migration to BI tools did not compromise the reliability of the data presented since it comes from our official source of information. The granularity of the Dashboard might seemed limited for the operational eye, however, increasing it would not be an option since the scope of the dashboard is limited to the main users interests. The operational details were covered using different tools such as PiSystem. If interested you can check the work on real-time dashboards and analysis on this repository: *include the repository on pisystem 
