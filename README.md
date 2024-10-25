# D365-Case-Data-Simulator
A robust case data simulator for D365 Customer Service. This collection of Power Platform Assets and documentation that will allow you to automate case data being populated in your D365 Customer Service environment so some of your Case related dashboards light up. 

Complete installation and administration documentation can be found here: [https://orange-sand-01b756b10.5.azurestaticapps.net/](https://orange-sand-01b756b10.5.azurestaticapps.net/)

Case Data Simulator - Core

- CaseDataSimulatorSolutionCore
- Is comprised of 2 Power Automate Cloud Flows and a Microsoft Dataverse Connection Reference
- These Cloud Flows will run at regularly scheduled intervals and create Cases with randomized data assigned to random users, then resolve the cases at somewhat random intervals
- Cloud Flows that will be created are:
    a. Case Data Simulator - Create New Cases Each Business Hour
    b. Case Data Simulator - Resolve Cases

Case Data Simulator - Optional - The purpose of it is to automate taking Surveys post case closure.

- CaseDataSimulatorSolutionOptional
- Its comprised of 1 Power Automate Cloud Flow, 3 Desktop Automations and 1 Connection Reference
- The Cloud Flow will run at regularly scheduled intervals, it selects a set of survey invitations related to the cases that were created, then uses Power Automate Desktop to take the survey
