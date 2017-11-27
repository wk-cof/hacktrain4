# Geo Incident
![Logo](https://github.com/wk-cof/hacktrain4/blob/master/src/assets/logo.png "Geo Incident Logo")

> HackTrain4.0 hackathon project

## Project overview

This project attempts to visualize the Historic Delay Attribution data from Network Rail in order to understand the impact of a single delay on the entire rail network.

## Data

Network Rail provides [Historic Delay Attribution data](https://www.networkrail.co.uk/who-we-are/transparency-and-ethics/transparency/datasets/) in CSV formats. We imported the data into a mysql database in [this project](https://github.com/vgorin/trainhack4) to provide an easy to use API for this front-end.

## Technology stack
VueJS + Webpack + Babel.


## Devpost
https://devpost.com/software/geo_incident

## Project Description
We have created a dynamic incident and delay time visualisation tool. The inspiration for this project is to help train operations manager visualise and understand network effects of a single incident on train lines.

The operator can use the platform to search the real-time TRUST database for the train that has been involved in an incident and specify the type of incident which has occurred. Our platform then draws on a database (through a database API we have developed) of passed incident data and finds similar incidents according to a range of proxies (location, line, time, day, incident type etc.).

Using multiple similar incidences, the platform predicts the network delays which may occur on all nodes in the rail network. Currently, Network Rail only measures the network effects on the primary nodes affected by the incidence, our platform reports on delays on all nodes in the system.

Using the data, we predict the length of the expected delay at each node and the probability of that delay occurring at the node in question. Using the GUI, the user can browse through nodes and see this data related to each node. The platform also notifies the user of critical nodes (nodes with the highest ratio of ‘expected delays’ to ‘time to delay occurrence’ at the node) and allows the user to inspect which lines at the node are most critical and require immediate action. Using this data, the train operations manager can both inform train operators of expected delays and attend to most critical lines and nodes in the network. This will improve the customer experience and decrease delay times over the network – which has significant financial implications on Network Rails operations.

We have developed a plan for implementation of the platform which accounts for future change in policies, human-centred considerations and critical stakeholders. The developed solution is an MVP, we have suggested future improvements to the system which will transform it into a robust analysis tool which is capable of tangible impact in the rail industry.