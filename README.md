# D365-Case-Data-Simulator
A robust case data simulator for D365 Customer Service. This collection of Power Platform Assets and documentation that will allow you to automate case data being populated in your D365 Customer Service environment so some of your Case related dashboards light up. 

Case Data Simulator - Core

- CaseDataSimulatorSolutionCore
- Is comprised of 2 Power Automate Cloud Flows and a Microsoft Dataverse Connection Reference
- These Cloud Flows will run at regularly scheduled intervals and create Cases with randomized data assigned to random users, then resolve the cases at somewhat random intervals
- Cloud Flows that will be created are:
    a. Case Data Simulator - Create New Cases Each Business Hour
    b. Case Data Simulator - Resolve Cases
- Follow the instructions to import the Solution https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions
- Create a field in your Case (Incident) table called “Demo Data Simulator” as a Yes/No Choice type field
- If you don't have much data in your D365 environment you may want to install Sample Data. Sample data will provide you with Users in order to assign the cases to.
- Its not required to install Sample data should you want to create your own users -or- if you have existing users in Dataverse
    a. https://learn.microsoft.com/en-us/power-platform/admin/add-remove-sample-data
- Following importing the solution you will need to make modifications to the Arrays within each Cloud Flow. Some of the Arrays hold values that are unique to each Dataverse instance such as record Identifiers/GUIDs. Others hold static values that can be modified directly within the Array of the Cloud Flow. 
- The way the Cloud Flow works is it selects random values from the Arrays and uses those values when creating a new Case record.
- For example, the CaseTitles Array will hold values that you will use for the titles of the Cases. The CaseType array holds a numeric value that maps to the a choice field for the type of the Case.
- Contact and Owner arrays contain GUIDs. You will need to retrieve these from Dataverse.
    - To retrieve owner (User) GUIDs - https://www.crminnovation.com/blog/find-a-users-guid-without-code/
    - To retrieve contact GUIDs - In Dataverse, view your Contact table data, make sure the "Contact" field is viewable
    - You can copy/paste the GUIDs in to the array

Case Data Simulator - Optional

- Please note, this solution is optional. The purpose of it is to automate taking Surveys post case closure.

- CaseDataSimulatorSolutionOptional
- Its comprised of 1 Power Automate Cloud Flow, 3 Desktop Automations and 1 Connection Reference
- The Cloud Flow will run at regularly scheduled intervals, it selects a set of survey invitations related to the cases that were created, then uses Power Automate Desktop to take the survey
- Just like in the Core solution, there are Arrays that need to be adjusted in the Cloud Flow.
- The Power Desktop Automation uses Chrome - You will need to ensure that Chrome is installed on the machine running the automation in addition to the Browser Extensions for Power Automate.
- The Customer Voice Survey will need to have the following three questions in this order:
    1. NPS
    2. Rating (Use Number)
    3. Text

- Create 2 Satisfaction Metrics, Sentiment and CSAT
    1. Bind Sentiment Satisfaction Metric to Question #3 (Text)
    2. Bind CSAT Satisfaction Metric to Question #2 (Rating)