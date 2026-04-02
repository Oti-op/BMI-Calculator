// Deployment issue and fix 
While deploying this react BMI calculator to Azure Static Web Apps, I encountered a build failure during the Github Action workflow

//Problem
The deployment failed with the error: "The app build failed to produce artifact folder: 'build'"

//Cause
The project was built using vite, which outputs production filed to a dist. folder by default. However, azure static web apps was configured to look
for a build/ folder (the default for Create React APP projects)

//Solution
I updated the Github Actions Workflow configuration file:
.github/workflow/azure/static-web-apps-*.yml

changed: output_location: build
to: output_location: dist

This resolved the issue, and the application deployed successfully

