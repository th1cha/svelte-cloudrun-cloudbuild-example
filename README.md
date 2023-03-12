# Svelte + Vite to CloudRun + CloudBuild
This is an example Svelte application that demonstrates how to deploy a container to GCP Cloud Run using Cloud Build.
## On repository
1. Create a new svelte app and push to your repository.
2. Add a Dockerfile to define config of your container image.
3. Add a 'cloudbuild.yaml' file to define the steps for building and deploying a application to cloudrun. 
Your 'cloudbuild.yaml' file should contain the following sections:
    - Build the container image.
    - Push the container image to the Container Registry.
    - Deploy the container image to Cloud Run

## Setting up GCP Cloud Build 
1. Goto Cloud Build console and connect your repository to Cloud Build
2. Create a new trigger for your repository. To do this, select the "Triggers" tab and click on the "Create Trigger" button. In the trigger configuration settings, specify the following:
    - Repository source: Select the repository you want to build from the dropdown menu.
    - Branch name: Specify the name of the branch you want to trigger builds for. You can also specify a regular expression to match multiple branches. 
    - Set the configuration type: You can do this by selecting the "Cloud Build configuration file" option and specifying the location of your configuration file, such as a cloudbuild.yaml or cloudbuild.json file.
    - Add any necessary substitution variables to your trigger settings. In example need to add variable name "_SERVICE_NAME"
    - Save and create the triger.

## Setting up GCP IAM
1. Navigate to the IAM section 
2. Click on the "Edit" button next to the principal name for your default Cloud Build service account. The principal name should be in the format '1234567@cloudbuild.gserviceaccount.com'
3. Assign Cloud Build Service Account, Cloud Run Admin, Cloud Run Service Agent to roles.


**Back to Clound Build and Try to "Run Trigger" to initiate a new build. If the build is successful, Cloud Build will push your container image to Container Registry and deploy it to Cloud Run.**

	

