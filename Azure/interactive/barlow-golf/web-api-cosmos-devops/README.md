# Azure Training - Barlow Golf - Modern Web Application with CI/CD

1. Azure Web App
   1. React App
2. Azure Functions
   1. c#
   2. Cosmos DB
3. DevOps
   1. Azure Boards
   2. Azure Repos
      1. Git
4. Azure Pipelines
   1. ARM Templates
   2. Build Pipelines
   3. Release Pipelines

## Background Details

Barlow Golf has a just completed its initial web application. The application is primarily a static website used for marketing and announcements. They have had a number of issues with the application and every time they try to add a new feature to the web application it is down for a few hours. They have decided to migrate their application to the Microsoft Azure cloud. They want to leverage Azure DevOps and build a modern deployment model while adding a few new features to the application.

## What will you be doing

1. Create a CI/CD Pipeline
2. Add features to the web application

## Architecture

The web application will be deployed to blob storage and served as a static website.
The web application will communicate with REST APIs which which are deployed as Azure Functions.
The database is utilizing Azures Cosmos DB for data storage.
